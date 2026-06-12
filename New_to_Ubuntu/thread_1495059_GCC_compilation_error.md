---
title: "GCC compilation error"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by jp8weaver on 2010-05-27
Hey All,
Alright, I'm probably definitely showing the fact that I have just started using this when I ask this question, but here goes. I am new to C programming, and I downloaded MinGW and installed it just fine. However, when I'm doing something as simple as a Hello World code, I'm getting some definite errors. In Notepad (yes, I'm using a dreaded Windows system) I wrote this, following a tutorial located at [http://www.math.wustl.edu/~sawyer/handouts/c_help.html:]("http://www.math.wustl.edu/%7Esawyer/handouts/c_help.html:") 

#include <stdio.h>
int main(void)
{printf("Hello, World!\n");
return 0 ;
}

Then saved it as Hello.c on my Desktop. I opened Command Prompt, changed the directory to the Desktop, and I'm sure my directory is right, but I got this error message after the code included: 

gcc -Wall Hello.c -o Hello
gcc: Hello.c: No such file or directory
gcc: no input files

I know I'm probably just missing some really simple section, but any help would be greatly appreciated! Thanks!

James

---

### Post by anglican on 2010-05-27
> **jp8weaver said:**
> Hey All,
Alright, I'm probably definitely showing the fact that I have just started using this when I ask this question, but here goes. I am new to C programming, and I downloaded MinGW and installed it just fine. However, when I'm doing something as simple as a Hello World code, I'm getting some definite errors. In Notepad (yes, I'm using a dreaded Windows system) I wrote this, following a tutorial located at [http://www.math.wustl.edu/~sawyer/handouts/c_help.html:]("http://www.math.wustl.edu/%7Esawyer/handouts/c_help.html:") 

#include <stdio.h>
int main(void)
{printf("Hello, World!\n");
return 0 ;
}

Then saved it as Hello.c on my Desktop. I opened Command Prompt, changed the directory to the Desktop, and I'm sure my directory is right, but I got this error message after the code included: 

gcc -Wall Hello.c -o Hello
gcc: Hello.c: No such file or directory
gcc: no input files

I know I'm probably just missing some really simple section, but any help would be greatly appreciated! Thanks!

James
Can you list the files with "ls -l"? You must have something wrong with the filename, if it was there gcc would find it.

H

---

### Post by jp8weaver on 2010-05-27
anglican, 
Thanks for the quick response! Okay, do you mean typing something like "gcc ls-l"? That just gives:
gcc: ls-l: No such file or directory
gcc: no input files

Thanks again,
James

---

### Post by anglican on 2010-05-27
> **jp8weaver said:**
> anglican, 
Thanks for the quick response! Okay, do you mean typing something like "gcc ls-l"? That just gives:
gcc: ls-l: No such file or directory
gcc: no input files

Thanks again,
James
No, just "ls -l" to list all the files in your current directory. perhaps you could post the output here.

H

---

### Post by jp8weaver on 2010-05-27
Alright, just typing "ls -l" gives:
'ls' is not recognized as an internal or external command, operable program or batch file.

Thanks!

---

### Post by anglican on 2010-05-27
> **jp8weaver said:**
> Alright, just typing "ls -l" gives:
'ls' is not recognized as an internal or external command, operable program or batch file.

Thanks!
Ah! Light dawns... I hadn't noticed that you're using Windows. Try "dir" instead, to list the files in that folder. This is a Linux forum, Windows questions are really best asked elsewhere!

H

---

### Post by anewguy on 2010-05-27
Hey, I use Mingw and msys as well as GTK in Windows so I keep things the same between Linux and Windows.  So, I understand if you installed mingw for that reason.  If, however, it was to get a free C compiler, I will offer you a solution that may be a little better for you in Windows:

- download Microsoft's free versions of Microsoft Visual Studio.  There you can get the free versions (non-commercial development) of the C/C++ IDE, the Visual Basic IDE, etc..  That way you would have a fully integrated development environment with the debugger, etc., all built in.  You can enter the code for your program and have it run within the IDE so you can debug, etc..  You can also do command line compilations though I prefer the IDE.

If you plan on doing cross-platform development, learn C and C++ or what ever you language of choice is first, then learn the cross-platform stuff like mingw and msys.

Dave ;)

---

### Post by jp8weaver on 2010-05-28
Hey Dave, 
Thanks for the reply, but I'll be doing some cross-platform stuff because my coworker for this project is using Linux. Just getting one step closer to working on a Linux machine myself. 

anglican,
Yeah, I had noticed that, but I wasn't 100% sure if it was a strictly Linux-based forum. ;) Anyway, I tried "dir" and got:
Volume in drive C has no label.

Directory of C:\Documents and Settings\weaver\Desktop

05/28/2010 08:19 AM <DIR> .
05/28/2010 08:19 AM <DIR> ..
05/27/2010 01:14 PM            76 hello.c.txt
05/25/2010 09:21 AM           786 Windows Media Player.lnk
2 File(s) 862 bytes
2 Dir(s) 138,924,158,976 bytes free

Thanks, again!

---

### Post by nikhilbhardwaj on 2010-05-28
there you have your answer
the file is named hello.c.txt instead of hello.c
try copy hello.c.txt hello.c
and then tryy compiling with gcc again.

---

### Post by jp8weaver on 2010-05-28
Alright, got it! The file was then named a.exe, and I've been told that it might be because I am just using Notepad for my editor, so I guess I will go to Visual Express, Dave. Thanks for the help!

James

---

### Post by anewguy on 2010-05-28
> **jp8weaver said:**
> Alright, got it! The file was then named a.exe, and I've been told that it might be because I am just using Notepad for my editor, so I guess I will go to Visual Express, Dave. Thanks for the help!

James

The Visual Express free editions will get you going in programming in a much easier (at least in my opinion) way than jumping in to programming at the editor/command line level.  A couple of notes:

You could save your source file from notepad as .c by changing the file type.

You can change the output executable name by including -o <name of executable> on the gcc line.  Example - putting -o hello on your gcc line would make the executable hello.exe.

I would definitely work on learning programming first before worrying about cross-platform development.  It's much easier if you know how to program first.  If your program is not GUI based, you can always port the source to Linux and try compiling there and learn what you may need to change.

Once you are ready for cross-platform development, start working with GTK for GUI'd applications.  You can get GTK for Windows (btw - it's free) to work on things there, then move to Linux and compile there (you will need to install the GTK development lib to do so).

Best of luck!  Welcome to programming, and welcome to Ubuntu!

Dave ;)

---

### Post by jp8weaver on 2010-05-28
Gotcha. Thanks! By the way, does Visual Express C++ also do C programming? My boss wanted me to write the program in C, rather than C++, so am I just missing something in the options within Visual Express C++? I have only been able to write C++ code in Visual Express, I think. Thanks, again!

James

---

### Post by anewguy on 2010-05-28
I haven't sat down to try actually write straight C in Visual Studio Express, but if worse comes to worse you can compile it at the command line using the Visual Studio compiler.  I may try opening a straight C program in Visual Studio Express later tonight just to see what it does.

Dave ;)

---

