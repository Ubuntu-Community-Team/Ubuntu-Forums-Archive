---
title: "What's a good, free C Comiler for a beginner?"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by RebeccaHowarth on 2008-12-20
I'm teaching myself C, and have been using Dev Bloodshed C/C++.  I like it, but am interested in learning about something new.  I'd appreciate any suggestions.

---

### Post by RebeccaHowarth on 2008-12-20
Oh, and just as a point of information, I have no idea why it's called "Bloodshed."  Funny name . . .

---

### Post by hailukah on 2008-12-20
There's the GNU C compiler and GNU C++ compiler.  They can be installed with 

sudo apt-get install build-essential

Information on them [here]("http://gcc.gnu.org/")

There is also the Tiny C Compiler

sudo apt-get install tcc

Information [here]("http://bellard.org/tcc/")

---

### Post by Kareeser on 2008-12-21
Actually, I believe gcc is installed automatically.

(Or if not, then it probably was during one of my random apt-get install binges...)

---

### Post by mbsullivan on 2008-12-21
To lend support to hailukah's thread, the *de facto* standard for free, portable C compilers is GCC. It is free (both free-as-in-beer and free-as-in-freedom), fairly highly optimizing and portable.

For general purposes, definitely go with GCC. The only exceptions to this are the following:
 (1) If the speed of compilation or size of the compiler is important
 (2) If you want to know what the compiler is doing (GCC is quite opaque)
 (3) If you don't want a GLPed compiler

Apart from those that hailukah mentioned, the only other one I would add is the "Portable C Compiler" (PCC). PCC may be preferable if you want to avoid the GPL, because it uses a more permissive (BSD) license.

Mike

---

### Post by RebeccaHowarth on 2008-12-21
> **Kareeser said:**
> Actually, I believe gcc is installed automatically.

(Or if not, then it probably was during one of my random apt-get install binges...)

Actually, yeah, it is, only I can't find it!  I've been looking for it for about 10 minutes.  Where is it?

Thanks for the replies, all!

---

### Post by not_yet on 2008-12-21
if you would like to try an IDE have a look at Eclipse

very powerful and free

has very good help features for beginners and lots of online help

[http://www.eclipse.org/](http://www.eclipse.org/)

---

### Post by Sorivenul on 2008-12-21
> **RebeccaHowarth said:**
> I've been looking for it for about 10 minutes.  Where is it?
```
locate gcc
```
> /usr/bin/gcc

For more information on getting started with Linux programming look at these Sticky threads:
[http://ubuntuforums.org/showthread.php?t=1006666]("http://ubuntuforums.org/showthread.php?t=1006666")
[http://ubuntuforums.org/showthread.php?t=1006662]("http://ubuntuforums.org/showthread.php?t=1006662")
Also, check out the Programming Talk subforum, as you will get better help, faster by posting specific needs there.  

You are probably looking for and IDE (Integrated Development Environment) to use as a frontend to GCC. There are plenty suggested in the links I provided, but my suggestions for new users falls to Code::Blocks, Anjuta, or Geany, all available in the repositories.  Eclipse is also good.  It comes down to personal choice.  Try a few and pick what suits you best.

EDIT: This thread will probably get moved to Programming Talk at some point. Also, if C is your choice as a first language you will probably get some suggestions to choose something like Python instead. [pmasiar's Learn Python wiki]("http://learnpython.pbwiki.com/") has some great information to get you started if you choose the Python route instead. Specifically, check out the "Why Python" link. If this is not your first language, disregard this statement. Again, the choice is yours.

---

### Post by RebeccaHowarth on 2008-12-21
Ok, so now I've put this program into Gedit:

```

#include<stdio.h>

int main(void){ 
     int counter; // Variable to loop from one to ten
     
    //The following loop will print numbers in a line from one to ten
     for(counter = 1; counter<11; counter++)
          printf("%d ", counter);
     
     return 0;
}
//main ends <return>


```

I saved it as firstcprog.c.  When I type gcc firstcprog.c into the terminal, it says:

gcc:  firstprog.c: No such file or directory
gcc:  no input files

As you can see, I'm really new to all this.  How do I compile and execute this program?  Thanks in advance for your patience!

---

### Post by Sorivenul on 2008-12-21
The command would look something like this:
```
gcc firstprog.c -o firstprog
```

The "-o" tells gcc what the name of the output executable should be.
Also, the command should be run in the directory of the program you are trying to compile.

To execute your new program, just type the program name, "firstprog" in this case, into the terminal while in the directory of the executable or with the path to the executable:
```
firstprog
```
or
```
/path/to/firstprog
```

For the GCC manual, in a terminal, type:
```
man gcc
```

---

### Post by namegame on 2008-12-21
Also make sure you are compiling in the same directory in which you saved your program.

---

### Post by Sorivenul on 2008-12-21
> **namegame said:**
> Also make sure you are compiling in the same directory in which you saved your program.
Already mentioned.  However, I forgot to say how to do it.
If the file is saved in your Home (/home) folder for example, you need to "change directory" to that location while in a terminal.  For example:
```
cd /home/rebecca
```

To get more familiar with the command-line in general look [here]("http://linuxcommand.org/") (linuxcommand.org), or [here]("http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/") (Ubuntu Cheat Sheet).

---

### Post by RebeccaHowarth on 2008-12-21
> **Sorivenul said:**
> Already mentioned.  However, I forgot to say how to do it.
If the file is saved in your Home (/home) folder for example, you need to "change directory" to that location while in a terminal.  For example:
```
cd /home/rebecca
```

To get more familiar with the command-line in general look [here]("http://linuxcommand.org/") (linuxcommand.org), or [here]("http://fosswire.com/2008/04/22/ubuntu-cheat-sheet/") (Ubuntu Cheat Sheet).

Ok, so I think this is my problem.  I saved the program in a folder within Documents.  What do I type for that?

---

### Post by Sorivenul on 2008-12-21
> **RebeccaHowarth said:**
> Ok, so I think this is my problem.  I saved the program in a folder within Documents.  What do I type for that?
Assuming your Home folder is named "rebecca":
```
cd /home/rebecca/Documents/name-of-folder-in-documents
```
Or shorter with:
```
cd ~/Documents/name-of-folder-in-documents
```

---

### Post by RebeccaHowarth on 2008-12-21
Alright, I have tried to figure this out, and I don't seem to be able to make it work.  I re-saved the program so that it's just in owner or "Home Folder."  I guess those are the same.  Here's what my terminal says:

owner@ubuntu:~$ cd /home/owner
owner@ubuntu:~$ gcc firstprog.c -o firstprog
gcc: firstprog.c: No such file or directory
gcc: no input files
owner@ubuntu:~$

---

### Post by Sorivenul on 2008-12-21
Did you check the spelling on the filename? Also remember this is case-sensitive, so FirstProg.c would be different than firstprog.c or firstprog.C.  Also, a common misspelling in the world "first" is to switch the r and the i around, make sure your program is named correctly and you are typing the command correctly.

---

