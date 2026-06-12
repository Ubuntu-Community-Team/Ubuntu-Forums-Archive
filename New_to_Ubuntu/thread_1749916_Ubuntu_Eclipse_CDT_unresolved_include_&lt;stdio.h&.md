---
title: "Ubuntu Eclipse CDT unresolved include &lt;stdio.h&gt;"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by ouou on 2011-05-05
Ubuntu 10.10 Ecelipse-cpp-helios-SR2-linux with eclipse-cdt
C and C++ project are fine
when i create a makefile project use #include for C or for C++
all gave unresolved inclusion: error, so that i can't build project
Please Help
I'm having trouble running C in eclipse. It first gives me weird syntax errors or tells me that
**include is an "Unresolved inclusion"**
 
It also will not let me build, saying "(Cannot run program "make": Launching failed)"
Am I missing something? please help.
Thanks

---

### Post by lkraemer on 2011-05-05
Your clue is "unresolved include <stdio.h>" ..............

When you compile code, you need the Headers and build-essential to be
able to get your compile completed.

Have you installed the Headers & build-essential?


Or maybe you don't have your libs included in your Eclipse setup.

Did you add the includes?

Select a Project, then PROJECT -> PROPERTIES ...............scroll down to...

C/C++ Build -> Settings .......then down to..............
TOOL SETTINGS -> GCC C Linker   ............... and check ALL OPTIONS:

Do you have anything here?

Then scroll down to GCC C Linker -> LIBRARIES and check -L ......

Do you have anything here?

Then your project should/will compile.


lk

---

