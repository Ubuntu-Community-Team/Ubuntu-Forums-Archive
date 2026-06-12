---
title: "how to use gcc?"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by Ghost_Programmer on 2010-03-06
recently i have shifted from xp to Ubuntu 9.10(64-bit). Can anybody please tell me how to compile and run c or c++ programs in Ubuntu? I don't understand much from it's documentation. I have a bit of idea of using Borland 5.5 on Win7(64). Is gcc somewhat similar to that?

Thank You.

---

### Post by ikt on 2010-03-06
> **Ghost_Programmer said:**
> recently i have shifted from xp to Ubuntu 9.10(64-bit). Can anybody please tell me how to compile and run c or c++ programs in Ubuntu? I don't understand much from it's documentation. I have a bit of idea of using Borland 5.5 on Win7(64). Is gcc somewhat similar to that?

Thank You.

Are you looking for help specifically about compiling programs or are you looking to just install programs?

---

### Post by Temposs on 2010-03-06
Open a terminal with Applications->Accessories->Terminal

You can use gcc in the following way:

```
gcc mycode.c -o myappname
```

So if you have your code in mycode.c, then an executable called myappname will be generated.

---

### Post by Ghost_Programmer on 2010-03-06
thanks , i tried that but it showed this
user@user-desktop:~$ gcc DTBS.C -o OP
/tmp/ccnjj8TX.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

here's the code:
#include<stdio.h> 
int main() 
{ 
int push(int [],int,int); 
int a[8],d,t=0,k; 
int pop(int t); 
printf("enter decimal no. "); 
scanf("%d",&d); 
 
while(d>0) 
{k=d%2; 
t=push(a,t,k); 
d/=2; 
} 
t--; 
printf("binary equivalent: "); 
while(t>=0) 
{ 
printf("%d",a[t]); 
t=pop(t); 
} 
return 0; 
} 
int push(int a[],int t,int k) 
{ 
a[t]=k; 
t++; 
return t; 
} 
int pop(int t) 
{ 
t--; 
return t; 
} 
 
can u pls help again?

---

### Post by howlingmadhowie on 2010-03-06
you need to first install the build-essential package. You can either do this over synaptic or by typing:
```

sudo apt-get install build-essential
<enter password>

```
at a terminal.

---

### Post by Ghost_Programmer on 2010-03-06
well i have already done that. anyway i did it again.it said "build-essential is already the newest version."

---

### Post by azagaros on 2010-03-06
first note:  void main(...) needs to be last in the source file.  Your functions need to be before main().

Once I made that change to your code it worked fine.

[PHP]#include <stdio.h>
#include <stdlib.h>

int push(int a[],int t,int k)
{
    a[t]=k;
    t++;
    return t;
}
int pop(int t)
{
    t--;
    return t;
}

int main()
{
    int push(int [],int,int);
    int a[8],d,t=0,k;
    int pop(int t);
    printf("enter decimal no. ");
    scanf("%d",&d);

    while(d>0)
    {
        k=d%2;
        t=push(a,t,k);
        d/=2;
    }
    t--;
    printf("binary equivalent: ");
    while(t>=0)
    {
        printf("%d",a[t]);
        t=pop(t);
    }
    return 0;
}

[/PHP]

hope that helps the beginner.

---

### Post by Ghost_Programmer on 2010-03-06
thanks, but i am sorry, it's just not working. it still shows the same error.
user@user-desktop:~$ gcc DTBS.C -o OP
/tmp/ccmseTWy.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

---

### Post by Temposs on 2010-03-06
Huh. I tried the version azagaros made and it worked fine on my machine...

---

### Post by Temposs on 2010-03-06
Well, try using g++ instead of gcc, and see if that makes a difference. I could use gcc with azagaros' code.

---

### Post by 3177 on 2010-03-06
is the # supposed to be there on the top lines?

---

### Post by Temposs on 2010-03-06
> **3177 said:**
> is the # supposed to be there on the top lines?

Yes, that is typical C/C++ syntax...

---

### Post by falconindy on 2010-03-06
gcc determines the type of compile that it needs to perform based on file extension -- '.C' is **not** the same as '.c'. Your code compiles fine when you alter the extension.

Alternatively, you can manually specify the language to compile with the '-x c' option.

---

### Post by lisati on 2010-03-06
> **Temposs said:**
> Huh. I tried the version azagaros made and it worked fine on my machine...

+1 azagaros's version compiled fine for me too.

I notice the OP seems to have the Desktop folder as the current working directory. Is gcc picking up the correct file to compile?

(Suggestion to OP: move each your programming projects to their own folders. Amongst other things, the Desktop folder has a special meaning: once you move on to larger projects, having all the files displaying on your desktop could get confusing in your everyday use of your system.)

---

### Post by Temposs on 2010-03-06
> **falconindy said:**
> gcc determines the type of compile that it needs to perform based on file extension -- '.C' is **not** the same as '.c'. Your code compiles fine when you alter the extension.

Alternatively, you can manually specify the language to compile with the '-x c' option.

+1 This is the solution :-)

---

### Post by agnes on 2010-03-06
You can also use "c++ yourfilename.cpp"

It's C++ code.
azagaros' version then worked for me. Otherwise I got the same error.

---

### Post by falconindy on 2010-03-06
> **agnes said:**
> You can also use "c++ yourfilename.cpp"

It's C++ code.
azagaros' version then worked for me. Otherwise I got the same error.

> #include<stdio.h> 
Doesn't look like C++ code to me. That's surely the standard I/O header for C.

---

### Post by azagaros on 2010-03-08
Most of the C++ compilers I know can compile c programs too, especially since the original create of C++ calls it C with objects..  The Standard has deviated from there though.

I do know that a .c and .C are two different flavors of C, but I don't know officially which is which though.

I find it interesting when a compiler barks at me when I do for either language.
[PHP]
     for(int nValue= 0; nValue < nAnotherValue; nValue++)
[/PHP]

and the C compiler spits back something about a c99 standard.  It expects the following for C.
[PHP]
     int nValue;
     for(nValue =0; nValue < nAnotherValue; nValue++)
[/PHP]

In the old days it didn't matter to the compilers.

---

### Post by agnes on 2010-03-08
> **falconindy said:**
> Doesn't look like C++ code to me. That's surely the standard I/O header for C.
It is the standard header for C, but C++ can use it fine too, since C++ includes stdio.h for compatibility reasons. When saying it was C++ I just meant it can be compiled correctly that way, although, looking back, I should have said "also C++" for correctness.

---

### Post by Green is Good on 2010-03-18
After another failed Ubuntu Update no.20 this time, had to reinstall over, now back to Ubuntu 9.10 via MS Windows XP Pro.

So after updating a fresh start!

1) I copied and pasted the updated program listed into gedit,
      then saved into the Documents directory and called the file DTBS.c

2) Then I opened Terminal,
      a) To find the file                              typed CD Documents
      b) To compile the file                     typed gcc -Wall DTBS.c -o DTBS
c) To run the Compiled file           typed ./DTBS

    3) Then followed the programs instructions on screen.

Note: -Wall is some kind of error checking, see the GCC Manual.

I would just like to say many thanks for this information, I now have used GCC to compile a C/C++ program and run the program.:popcorn:

---

