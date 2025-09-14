using System;
public class Pupil
{
    public virtual void Study()
    {
        Console.WriteLine("Ученик учится");
    }

    public virtual void Read()
    {
        Console.WriteLine("Ученик читает");
    }

    public virtual void Write()
    {
        Console.WriteLine("Ученик пишет");
    }

    public virtual void Relax()
    {
        Console.WriteLine("Ученик отдыхает");
    }
}

public class ExcelentPupil : Pupil
{
    public override void Study()
    {
        Console.WriteLine("Отличник усердно учится");
    }

    public override void Read()
    {
        Console.WriteLine("Отличник внимательно читает");
    }

    public override void Write()
    {
        Console.WriteLine("Отличник аккуратно пишет");
    }

    public override void Relax()
    {
        Console.WriteLine("Отличник немного отдыхает");
    }
}

public class GoodPupil : Pupil
{
    public override void Study()
    {
        Console.WriteLine("Хорошист старается учиться");
    }

    public override void Read()
    {
        Console.WriteLine("Хорошист читает с интересом");
    }

    public override void Write()
    {
        Console.WriteLine("Хорошист пишет аккуратно");
    }

    public override void Relax()
    {
        Console.WriteLine("Хорошист отдыхает");
    }
}

public class BadPupil : Pupil
{
    public override void Study()
    {
        Console.WriteLine("Двоечник не хочет учиться");
    }

    public override void Read()
    {
        Console.WriteLine("Двоечник читает невнимательно");
    }

    public override void Write()
    {
        Console.WriteLine("Двоечник пишет небрежно");
    }

    public override void Relax()
    {
        Console.WriteLine("Двоечник много отдыхает");
    }
}

public class ClassRoom
{
    private Pupil[] pupils;
    public ClassRoom(params Pupil[] pupils)
    {
        if (pupils.Length < 4)
        {
            this.pupils = new Pupil[4];
            Array.Copy(pupils, this.pupils, pupils.Length);
            for (int i = pupils.Length; i < 4; i++)
            {
                this.pupils[i] = new Pupil();
            }
        }
        else
        {
            this.pupils = pupils;
        }
    }
    public void ShowClassInfo()
    {

        for (int i = 0; i < pupils.Length; i++)
        {
            Console.WriteLine($"Ученик {i + 1}:");
            Console.Write("Учеба: "); pupils[i].Study();
            Console.Write("Чтение: "); pupils[i].Read();
            Console.Write("Письмо: "); pupils[i].Write();
            Console.Write("Отдых: "); pupils[i].Relax();
            Console.WriteLine();
        }
    }
}
class Program
{
    static void Main()
    {
        Console.WriteLine("Класс с 4 учениками:");
        ClassRoom class1 = new ClassRoom(
            new ExcelentPupil(),
            new GoodPupil(),
            new BadPupil(),
            new Pupil()
        );
        class1.ShowClassInfo();

        Console.WriteLine("Класс с 3 учениками:");
        ClassRoom class2 = new ClassRoom(
            new ExcelentPupil(),
            new GoodPupil(),
            new BadPupil()
        );
        class2.ShowClassInfo();

        Console.WriteLine("Класс с 2 учениками:");
        ClassRoom class3 = new ClassRoom(
            new ExcelentPupil(),
            new GoodPupil()
        );
        class3.ShowClassInfo();
    }
}





