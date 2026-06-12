---
title: "Can Linux programs be installed in Windows?"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by maf939 on 2010-09-15
Can Linux applications (.deb or .rpm packages) be installed in Windows?

---

### Post by jtarin on 2010-09-15
In the Windows operating system? No. In a virtual environment like WUBI? Yes.

---

### Post by cascade9 on 2010-09-15
I dont know about RPM or DEB files, but I have run at least some linux native programs in windows. Mucking around with WinGTK, PyGTK, etc can be fustrating though.

---

### Post by cgroza on 2010-09-15
Only when they will make something similar like wine for windows.

---

### Post by oldfred on 2010-09-15
But you can install windows versions of many programs like firefox, thunderbird, openoffice and use the same data from the linux versions. I prefer to have a shared NTFS partition for that.

---

### Post by Nythain on 2010-09-15
cygwin

---

### Post by snowpine on 2010-09-15
Many open source projects (Firefox, GIMP, OpenOffice, VLC, etc.) are also available for Windows and/or Mac.

---

### Post by maf939 on 2010-09-15
> **cgroza said:**
> Only when they will make something similar like wine for windows.

That is interesting, are there any programs like that in existence ? In my humble experience I haven't seen such program before

---

### Post by Nythain on 2010-09-15
> **maf939 said:**
> That is interesting, are there any programs like that in existence ? In my humble experience I haven't seen such program before
[http://www.cygwin.com/](http://www.cygwin.com/)

---

### Post by xebian on 2010-09-15
> **maf939 said:**
> **Can Linux applications (.deb or .rpm packages) be installed in Windows?**

Sure can on some.):P

---

### Post by dtfinch on 2010-09-15
I'd suggest Windows ports when possible, since most common programs have them. For the brave, there's also [andLinux](http://www.andlinux.org/) which runs Linux on top of Windows without needing a full system emulator like virtualbox. It's sort of like having a headless linux machine on the network that you access through ssh and Xming, letting you use Windows and Linux apps side by side, but running locally with extra desktop integration.

---

### Post by maf939 on 2010-09-15
> **Nythain said:**
> [http://www.cygwin.com/](http://www.cygwin.com/)

Cool !!! Thanks !!!

---

### Post by maf939 on 2010-09-15
> **dtfinch said:**
> ... For the brave, there's also [andLinux]("http://www.andlinux.org/") which runs Linux on top of Windows without needing a full system emulator like virtualbox...

Now I have 2 options: 
**cygwin** together with [B]andLinux

[/B]

---

### Post by lukeiamyourfather on 2010-09-15
> **Nythain said:**
> cygwin

> **[COLOR="DarkRed"]Cygwin is not a way to run native linux apps on Windows.[/COLOR]** You have to rebuild your application from source if you want it to run on Windows.

That's on their homepage, a common misconception.

[http://www.cygwin.com/](http://www.cygwin.com/)

The best option is probably a virtual machine like VirtualBox.

---

### Post by beew on 2010-09-15
I tried to set up cygwin many moons ago and it was hell. 

I find it a lot easier to actually install Linux (Ubuntu, Fedora, Debian) cygwin is like some monstrous version of WINE from the evil parallel universe except 100 times bigger and buggier. It  was broken and always complaining about missing dependencies and even when I did succeed in setting up some features strange bugs appeared like the drop down menus in X-windows never stayed open. T he instruction manual  might as well be written in ancient Greek.  So based on my admittedly limited experience unless you are a Unix pro forget about it.

---

### Post by DrMelon on 2010-09-15
The CoLinux project is interesting - it runs a tiny version of Linux inside an exe file, and behaves just like a virtual machine - but it integrates seamlessly with the desktop.

Based on CoLinux, funnily enough, is a project called "Portable Ubuntu". It's basically Ubuntu but in an exe file. Try it!
[http://sourceforge.net/projects/portableubuntu/](http://sourceforge.net/projects/portableubuntu/)

---

### Post by cgroza on 2010-09-15
Can you install deb pakages in cygwin? This is what the OP is looking for.

---

### Post by jadedcritic on 2010-09-15
> **dtfinch said:**
> I'd suggest Windows ports when possible, since most common programs have them. For the brave, there's also [andLinux](http://www.andlinux.org/) which runs Linux on top of Windows without needing a full system emulator like virtualbox. It's sort of like having a headless linux machine on the network that you access through ssh and Xming, letting you use Windows and Linux apps side by side, but running locally with extra desktop integration.

Tried Andlinux once.  Thought it was interesting, but it didn't go far enough in my mind.  Tell you what made me crazy was not being able to easily terminal output to the windows section of things.  The easy solution there is cygwin,  but I think Andlinux was more or less my attempt to get on the linux bus without ACTUALLY getting on the bus.

---

### Post by jtarin on 2010-09-15
Ported and installed are two different things.

---

### Post by maf939 on 2010-09-15
> **jtarin said:**
> Ported and installed are two different things.

I am aware of that point, The question was about real installation, not just porting.. I understand now that it is very difficult to *install* Linux programs in Windows environment. and it it needs expertise, patience and some programs like _cygwin_, _andLinux_ and _Colinux_ to *port* Linux programs into Windows. and that porting gives rather unpleasant results (as for now at least). I hope I am getting it right.

---

### Post by lukeiamyourfather on 2010-09-15
> **cgroza said:**
> Can you install deb pakages in cygwin? This is what the OP is looking for.

See my earlier post. The answer is no.

---

### Post by lukeiamyourfather on 2010-09-15
> **maf939 said:**
> I understand now that it is very difficult to *install* Linux programs in Windows environment.


Difficult is understatement. By difficult do you mean impossible?

> **maf939 said:**
> 
and that porting gives rather unpleasant results (as for now at least). I hope I am getting it right.

Porting means changing operating system specific stuff to make the software work in another environment and then compiling it again. For example there's applications like FileZilla, Firefox, VLC media player, and so on. They all have ports for Linux, Windows, and various other operating systems. They are not "unpleasant" but they are slightly different for each environment.

Porting something is not a trivial task and some stuff can't be ported at all. What are you actually trying to do? Knowing the root of the issue would help to resolve it, because you simply can't take a .deb or .rpm package and install it on Windows no matter how much effort you put into it.

---

### Post by jtarin on 2010-09-15
Bingo!!! Linux provides a way to install Windows applications,but the reverse is not true. The Linux community has all it can do to provide for users of Linux and developing Wine goes very far to get a lot of your Windows programs running under Linux.When MS decides to be as magnaminous the maybe it will be different. Installing Gimp for windows and the accompanying GTK widgets allows one to install a number of other GTK related apps. The development of QT also allows one to run KDE within windows.

---

### Post by maf939 on 2010-09-16
> **lukeiamyourfather said:**
>  because you simply can't take a .deb or .rpm package and install it on Windows no matter how much effort you put into it.


I think this is the most accurate answer to the question.

---

### Post by xebian on 2010-09-16
> **maf939 said:**
> I think this is the most accurate answer to the question.

Not exactly true.  A .deb or .rpm file is just another archive.  And if the application is written in say c++, or java, or python, they can run in windows with a little/big effort.

---

### Post by maf939 on 2010-09-16
> **xebian said:**
> Not exactly true.  A .deb or .rpm file is just another archive.  And if the application is written in say c++, or java, or python, they can run in windows with a little/big effort.

Thanks.

---

### Post by anewguy on 2010-09-16
I'll throw my 2 cents worth in here as well.  I've developed programs in C/C++ using GTK+, and with just a couple of ifdef in the source the same source can be used in Windows and Linux.  I usually add MingW and MSys to Windows so I can compile in an environment that looks common.  Add to that things like the libusb port to Windows, and a lot of things are possible.

But, as has been mentioned here many times, the likelyhood of any .deb, etc., file being able to be installed in Windows is extremely slim.  Running the Linux executable included in such a package - probably impossible.

Common source code, common packages (like GTK+, libusb, ffmpeg, etc.) can allow applications to be run on both systems from the same source code, but the code must be compiled on each system.

That, anyway, has been my limited experience.

Dave ;)

---

### Post by andrew.46 on 2010-09-17
Hi Dave,

> **anewguy said:**
> Common source code, common packages (like GTK+, libusb, ffmpeg, etc.) can allow applications to be run on both systems from the same source code, but the code must be compiled on each system.

Exactly! This can be a struggle as it often a path little travelled. I personally spent some considerable time and effort compiling the source code for the newsreader slrn on Windows 7 and documented it here:

Compiling the Subversion slrn under Windows 7
[http://www.andrews-corner.org/slrn-windows.html](http://www.andrews-corner.org/slrn-windows.html)

So not often the most straightforward process but it certainly can be done :).

Andrew

---

### Post by KROwen1959 on 2010-09-17
If windows was as easy as Linux/Ubuntu then this O S would not exist. The whole idea was to make it when anyone can add to or take away without destroying the O S. Windows O S is locked and unless you are programmer any changes you make will mess it up. You CAN'T put Linux on Windows but you CAN put Windows on Linux

---

### Post by mastablasta on 2010-09-17
> **KROwen1959 said:**
>  Windows O S is locked and unless you are programmer any changes you make will mess it up. 
 
really? and if you do changes in Linux you won't mess it up?
 
> You CAN'T put Linux on Windows but you CAN put Windows on Linux
 
you don't really need Linux applications in windows as they offer you enough of applications that run under windows. which is not true on the opposite side as large number of applications don't run (yet?!) in Linux. a good example are games where you have a huge number of quality games in windows while in linux there is only a fraction of them. and most with good graphics for example are already old...
 
then there is photoshop and MS Office that both set the standards these days. In fact OOo wants to be like/close alternative to MS Office.

---

### Post by maf939 on 2010-09-17
> **mastablasta said:**
>  you don't really need Linux applications in windows as they offer you enough of applications that run under windows. which is not true on the opposite side as large number of applications don't run (yet?!) in Linux. a good example are games where you have a huge number of quality games in windows while in linux there is only a fraction of them. and most with good graphics for example are already old...
 
then there is Photoshop and MS Office that both set the standards these days. In fact OOo wants to be like/close alternative to MS Office.

I agree with that, as a matter of fact I am still having Windows next to Ubuntu just because of 2 things: First, I need MS Office for my work (medical publishing) and OOo is just not enough (yet). And second, I am a hardcore gamer with special predilection for FPS, any gamer around here would feel the suffering I would have if I was deprived from Windows.

P.S. I think it is not the fault of Linux not being a games platform, in fact it is a good one, Open GL rendering is as good as Direct X. It is the fault of game manufacturers who do not port games to Linux :mad:.

---

