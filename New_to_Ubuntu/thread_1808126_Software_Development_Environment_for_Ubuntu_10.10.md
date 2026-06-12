---
title: "Software Development Environment for Ubuntu 10.10"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by J Hildreth on 2011-07-19
I am new to Linux.  I have just installed Ubuntu 10.10 from a Linux Identity magazine DVD and am interested in experimenting with code and application development for the Linux OS.  My basic question is this:  What development environment would be best for me to use?
 

 Some description of my background with computers and programming would likely be helpful in formulating responses.  I have been working with computers for about 40 years.  My experience goes back to the days when punched cards (remember those?  Face down, 9 edge forward!) were the only means of input; well there was punched tape and binary switches I guess.  I got into personal computers with the Apple II+ and migrated into Intel x86 machines when DOS 3 was the hottest thing going.  I have suffered through the numerous releases of MS Windows and have finally decided to explore the Linux open OS environment.
 

 My programming experience began with Fortran 3 and early Basic.  Over the past 20+ years I have become “familiar” with the C and C++ languages and development environments such as MS Visual Studio and the Borland Windows development products.  I use the term “familiar” in that I know enough to be dangerous. But by no means do I qualify as a professional programmer.
 

 The Ubuntu OS I installed came with 4 products that appear to have some of the software development capabilities I am looking for.  These products are QT Assistant, versions 3 and 4, QT4 Designer and QT4 Linguist.  Before I spend a significant amount of time going through the documentation of these tools, I thought I would post my question on this forum and try to tap the large amount of experience and information that I am certain exists here.  Your comments and recommendations would be appreciated.
 

 Joe

---

### Post by Mr. Shannon on 2011-07-20
Welcome to the forms.  I am getting my minor in computer science and am taking data structures at the moment so that might tell you how much you can trust my answer (in other words, I'm pretty new  programming where you type text in).

Considering where you started you probably won't find this as outdated and arcane as some do.  As much as I have heard, the typical way to program C/C++ on Linux is to use a text editor (**vim**/**emacs**/**gedit**...) and compile with **g++**.  A **makefile** is used for anything large.  It is essentially a set of instruction on how to call g++ to compile and link your program.  The manual for** GNU make** can be found at this [[COLOR="Blue"]link[/COLOR]]("http://www.gnu.org/software/make/manual/").  When doing things this way **GDB** is usually used for debugging.  I use **vim** for my text editor, compile with **g++** and **makefiles**, use **Nemiver** (a graphical front end to GDB) for debugging and **screen** to tile my terminal so I can have multiple editors and bash windows side by side without actually having multiple gnome terminals open.

IDE's for Linux are not completely uncommon.  I have tried several and found most too hard to use or I could not get them to compile a program.  You may want to try these out and see for yourself though:** Code::Blocks**, **Eclipse**, **Anjuta**, **NetBeans**, **Geany**, and **Qt Creator**.  I've tried the first four of these, the second two I could not get to work, and the second one I found to be too complex.  I have given thought to using Code::Blocks instead of the method that I described above but I need spell check and to install spell check in Code::Blocks you have to compile the plugin from source (never got that working).  As a side note, Eclipse does come with spell check.

Up to this point I have not talked about making graphical programs.  In Linux there are two main libraries for doing this: **Qt** and **GTK+**/**gtkmm**.  wxWidgets could be included as well but it is less popular.  Now to explain what these are.  **Qt** is a C++ library for making graphical applications (among other things) for the **KDE** desktop environment.  **GTK+**/**gtkmm** (the first is C and the second is C++) are for making graphical applications for the **GNOME** desktop environment (this is the native desktop environment in Ubuntu).  NOTE: **Qt** applications will run in **GNOME** and **GTK**/**gtkmm** applications will run in **KDE**, they just don't always look as good when not in there native desktop environment.  Now, you can use an IDE and/or graphical design program (**Qt Designer**/**Glade**) to make programs in these or you can do everything the old fashion way as described above (not sure about **Qt** since it has to be compiled differently).

I'v covered a lot of what's out there so now pick which method works for you.

By the way, when my mom was in college she used punch cards when writing in COBOL.

---

### Post by wep940 on 2011-07-20
Jeez, you guys are making me feel pretty old!
 
Just a small addition to what has already been posted (a very good post) I would just say that I have used GTK for GUI development in C in Ubuntu and have been able to get the same source to compile and run in Windows (requires MingW and GTK for Windows).  You may want to keep that in mind if you might want to develop cross-platform.  Though I have never used it, I believe Java is cross-platform as well and it can use GTK.  Some would probably say the open source Java equivalent (forgive me, but I'm drawing a blank on the name - and it was just in my mind!) also supports GTK and is availabe for Windows as well.
 
I'm not that knowledgable on other tools so I can only speak of what I've used.  If you are interested, I could send you some C code that uses GTK for you to peruse.  This code also uses some low level calls for USB handling as it was used for some non-standard cameras/camcorders that are no longer being made.  You can just ignore most of the code and just look at the GTK stuff - it sets up a GUI'd screen that has a few choices on it that toggle an action.  There is code for posting error messages, etc., back into that screen as well.

---

