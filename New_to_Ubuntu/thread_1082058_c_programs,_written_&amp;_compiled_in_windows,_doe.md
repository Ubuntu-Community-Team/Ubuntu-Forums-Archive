---
title: "c programs, written &amp; compiled in windows, doesn't run in linux"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by munishvit on 2009-02-27
I wrote some C programs, when i use to use windows. they worked fine then. But i tried to run those programs in ubuntu terminal, but in vain. Following is one of the program:

#include<stdio.h>
#include<conio.h>
#include<math.h>
void main ()
{
double A, B, Sum, Dif, Mult, Div;
clrscr();
printf("Enter the values of A & B (both are double type variables)\n");
printf("A = ");
scanf("%lf", &A);
printf("B = ");
scanf("%lf", &B);
printf("\nYou just enter the values\nA = %lf\nB = %lf\n", A, B);
Sum = A+B;
Dif = A-B;
Mult = A*B;
Div = A/B;
printf("\nSum = %lf\nDif = %lf\nMult = %lf\nDiv = %lf\n", Sum, Dif, Mult, Div);
getch();
}

---

### Post by pedro_orange on 2009-02-27
Do you have gcc installed? If not:

```
sudo apt-get install build-essential
```

You then need to compile it with a command like:

```
gcc input.c -o output.o
```

And then you run it like

```
./output.o
```

I expect you're trying to run them as exe? If you want to run exe you need to use wine.

```
sudo apt-get install wine
```

But that will just make them run slower. Use GCC!

---

### Post by Mark Phelps on 2009-02-27
You mean you can't compile and run it in Linux? Or, you mean that the executable you made in MS Windows won't work in Linux?

If the latter, you need to realize that Linux is not Windows.  Any source you have will need to be recompiled and relinked in order to run in Linux.

---

### Post by Shpongle on 2009-02-27
check out my thread and you can set up gedit 

to compile & run for you

[http://ubuntuforums.org/showthread.php?t=1073795](http://ubuntuforums.org/showthread.php?t=1073795)

---

### Post by munishvit on 2009-02-27
> **pedro_orange said:**
> Do you have gcc installed? If not:

```
sudo apt-get install build-essential
```

You then need to compile it with a command like:

```
gcc input.c -o output.o
```

And then you run it like

```
./output.o
```

I expect you're trying to run them as exe? If you want to run exe you need to use wine.

```
sudo apt-get install wine
```

But that will just make them run slower. Use GCC!

munish@lappy:~$ gcc asmd.c -o output.o
while compiling m getting following error messages:
asmd.c:2:18: error: conio.h: No such file or directory
asmd.c: In function ‘main’:
asmd.c:5: warning: return type of ‘main’ is not ‘int’

---

### Post by feelshift on 2009-02-27
> asmd.c: In function ‘main’:
asmd.c:5: warning: return type of ‘main’ is not ‘int’ 
Try "int main()" instead of "void main()" and then add a "return(0);" after "getch();".

---

### Post by Tony Flury on 2009-02-27
and as far as I know conio.h is a Windows only header file - and is not portable.

---

### Post by ChaiTan on 2009-02-27
From the header file conio.h and functions clrscr and getch, im assuming that you used TC to write the programs in windows. TC is non-standard.
So for compiling it in gcc, remove include line for conio.h and also clrscr and getch.
And also change void main to int main, and enter return 0; at the end of the program.

---

