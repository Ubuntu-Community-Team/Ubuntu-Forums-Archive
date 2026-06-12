---
title: "NS2 Path environment variable"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by yperionas on 2009-09-06
I am a new user to linux and im a bit confused with Path enviroment variables. So i need a small help to make things a bit more clear.

I've installed ns2 and i edited ~/.bashrc  to write the path as denoted at the end of ns2 installation.

For what i am confused is that i made a copy of th original ns2 installation in order to do modification in the source code. And when i go to this ns2 copy main folder where ns2 executable is and i run it, it runs the executable of the original ns2 folder, eventhough that copy folder has a different path.

If for example original is: ns2/ns-allinone-2.33/ns-2.33/
the copy is: nsmod/ns-allinone-2.33/ns-2.33/

Any idea why this is happening and how i can fix it?

I know i could run the executables locally by typing ./ns myfile.tcl  but i was wondering if i can set it inside bashrc.

I also tried to make a copy of the existing environment variables of ns2 and change ns2 with nsmod in the path but didnt change much.

Thanks for your comments and help in advance.

---

### Post by jeppewinther on 2009-09-06
If I am understanding you correctly, this would be the expected and correct behaviour.

When you edit the PATH variable, you're effectively telling the system to recognize a given command and run it in a consistent way no matter your current location in the filesystem. Like you can with all the other commands you can issue in the terminal, such as LS, CD and so on.

And you also list the solution yourself, which is to run "./command" (this local command), instead of "command" (that global command).


Is there some issue here I didn't pick up on?

---

### Post by yperionas on 2009-09-07
_Question 1_: Can i change somehow the Path environment variable so that when i'm either in one of the following directories i can simply run ns2 by typing: ns myfile.tcl ?

ns2/ns-allinone-2.33/ns-2.33/
nsmod/ns-allinone-2.33/ns-2.33/

_Question 2_: 

Im in ns2/ns-allinone-2.33/ns-2.33/ directory in which myfile.tcl exists and also ns (executable, since make compiled the source code successfully)

I run: ns myfile.tcl and i get: myfile.tcl does not exist, try again (which means i cannot find the path it resides?)

But in bashrc i have included:
PATH=$PATH:/home/lefteris/ns2/ns-allinone-2.33/bin:/home/lefteris/ns2/ns-allinone-2.33/tcl8.4.18/unix:/home/lefteris/ns2/ns-allinone-2.33/tk8.4.18/unix:/home/lefteris/ns2/ns-allinone-2.33/nam-1.13/

export PATH

export LD_LIBRARY_PATH=/home/lefteris/ns2/ns-allinone-2.33/otcl-1.13:/home/lefteris/ns2/ns-allinone-2.33/lib

export TCL_LIBRARY=/home/lefteris/ns2/ns-allinone-2.33/tcl8.4.18/library

What am i missing?

---

