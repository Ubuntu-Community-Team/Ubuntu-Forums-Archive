---
title: "8051compiler for ubuntu"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by A_M_S on 2010-04-17
Hello.

Anybody know a 8051 C and assembler compiler for Ubuntu preferably with a GUI?

Tnx.

---

### Post by quadproc on 2010-04-17
> **A_M_S said:**
> Hello.

Anybody know a 8051 C and assembler compiler for Ubuntu preferably with a GUI?

Tnx.
It is pretty unlikely that a C compiler exists for the 8051 due to the nature of that processor and its typical applications. For example, consider the implications of a C statement such as ```
printf("some output %s %n", textbufferpointer, somedecimalvariable - 0.5); 
```A compiler for this would have to produce code that does IO, allocates and deallocates a text buffer, does decimal arithmetic, evaluates decimal numeric expressions, handles interrupts, and a lot of other things.

There are a number of 8051 assemblers around, and a good macro assembler can provide almost the same programming ease as a compiler if you have a good application library available.

quadproc

---

### Post by A_M_S on 2010-04-18
> **quadproc said:**
> It is pretty unlikely that a C compiler exists for the 8051 due to the nature of that processor and its typical applications. For example, consider the implications of a C statement such as ```
printf("some output %s %n", textbufferpointer, somedecimalvariable - 0.5); 
```A compiler for this would have to produce code that does IO, allocates and deallocates a text buffer, does decimal arithmetic, evaluates decimal numeric expressions, handles interrupts, and a lot of other things.

There are a number of 8051 assemblers around, and a good macro assembler can provide almost the same programming ease as a compiler if you have a good application library available.

quadproc

Thank you for the reply.

There are 8051 C compilers. I worked with some in windows.

I was looking for a user friendly GUI for teaching purposes.

The links below are promising. 

 [http://mcu8051ide.sourceforge.net/intro]("http://mcu8051ide.sourceforge.net/intro")

[http://sdcc.sourceforge.net/index.php]("http://sdcc.sourceforge.net/index.php")

---

### Post by gmargo on 2010-04-18
[SIZE=2]This looks interesting.  Not open source but it's java.
[FONT=Arial, Helvetica, sans-serif]"The 8051 Simulator for Teachers and Students"[/FONT]
[http://www.edsim51.com/](http://www.edsim51.com/)[/SIZE]

---

### Post by A_M_S on 2010-04-19
> **gmargo said:**
> [SIZE=2]This looks interesting.  Not open source but it's java.
[FONT=Arial, Helvetica, sans-serif]"The 8051 Simulator for Teachers and Students"[/FONT]
[http://www.edsim51.com/](http://www.edsim51.com/)[/SIZE]


Yes its very good for learning purposes. 
I'm using it.
Unfortunately doesn't support natively C. 

Regards

---

### Post by SRST Technologies on 2010-04-19
This is barely related to subject at all, but are you looking for an 8501 compiler to make NES ROMs?  I have found that the xa compiler in the repos for Fedora 12 do not produce usable results.

---

### Post by A_M_S on 2010-04-23
> **SRST Technologies said:**
> This is barely related to subject at all, but are you looking for an 8501 compiler to make NES ROMs? .
Nope.

---

### Post by anewguy on 2010-04-23
I think I would try the Small Device C Compiler (it's the sdcc link you mentioned above).  Part of the reason I would do so is that it is available for both Windows and Linux, and it's free.  This would mean you could use the same compiler on both platforms, which to me would be easier.  I use GTK+ and C, and using the MingW, Msys, and GTK for Windows downloads (free) I am able to compile the source code on both platforms with only a couple of #ifdef statements where needed to differentiate between Windows and Linux (and thanks to MingW, Msys, pkg-config in Windows, I am able to use gcc for compiling on both platforms).  I don't know if you would need such things for cross compiling with SDCC or not.

Dave ;)

---

