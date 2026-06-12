---
title: "[SOLVED] Should I use Xubuntu 8.10 or Fedora 10 for SLOW iBook G3?"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by NewsAndHistory on 2009-01-11
Please tell me which version of Xubuntu would work on an old iBook G3 (Processor: 600 MHz PowerPC)?

_*2 more questions*_:
Is Xubuntu 8.10 (Intrepid) ***faster*** than 8.4.1 (Hardy Heron)?
Which of these versions works on PowerPC (PPC) computers: i686 or x86 (amd64)?

I need an operating system that will work faster than Panther OS X 10.3.9. That's why I'm trying to find out whether Xubuntu or Fedora would run better on my old iBook.

---

### Post by avtolle on 2009-01-11
You will need to go over to the Apple Users subforum for best answers to your questions. As to downloading the correct iso, you will need to get the ppc version of each; on the Apple Users subforum, there is a sticky which will direct you to the right place for Ubuntu. Don't know what to tell you for Xubuntu; have you been to [http://www.xubuntu.org](http://www.xubuntu.org) to check?

I'm using both 8.04 and 8.10 Ubuntu on two G4 Cubes, 450 mhz processors, both of which have RAM upgraded; no appreciable difference in speed that I've noticed. BTW, the amount of RAM is more important than the speed of your processor, IMO, in determining how fast a certain distro will run. HTH.

---

### Post by igknighted on 2009-01-11
It doesn't matter what distro you choose, all that matters is what software you run.  The software choices are the same either way.

I would choose yellow dog linux (ydl) for PPC computers, but that's just me.

---

### Post by Xiong Chiamiov on 2009-01-11
> **NewsAndHistory said:**
> Which of these versions works on PowerPC (PPC) computers: i686 or x86 (amd64)?
Neither.  Those are 32-bit and 64-bit Intel processor types.

---

### Post by avtolle on 2009-01-11
@NewsAndHistory: try [http://cdimage.ubuntu.com/xubuntu/ports/releases/](http://cdimage.ubuntu.com/xubuntu/ports/releases/) for ppc releases of Xubuntu.

---

### Post by Frak on 2009-01-11
In my humble opinion, I'd rather use YDL on a G3 than Xubuntu. The difference in speed between the two is noticeable, and YDL is exclusively developed for PPC (G3, G4, G5 Mac) machines.

---

### Post by mjheagle8 on 2009-01-11
i'd say yellow dog also. something designed exclusively for the hardware type you use is almost always faster, safer, and overall superior.

---

### Post by avtolle on 2009-01-11
And, I agree; for maximum performance, YDL is your best bet.

---

### Post by NewsAndHistory on 2009-01-12
> **avtolle said:**
> You will need to go over to the Apple Users subforum for best answers to your questions. As to downloading the correct iso, you will need to get the ppc version of each; on the Apple Users subforum, there is a sticky which will direct you to the right place for Ubuntu. Don't know what to tell you for Xubuntu; have you been to [http://www.xubuntu.org](http://www.xubuntu.org) to check?

I'm using both 8.04 and 8.10 Ubuntu on two G4 Cubes, 450 mhz processors, both of which have RAM upgraded; no appreciable difference in speed that I've noticed. BTW, the amount of RAM is more important than the speed of your processor, IMO, in determining how fast a certain distro will run. HTH.

OK, I'll go back to that subforum, tonight. I've been to the Xubuntu website a few times, but I didn't see PPC listed as an option when I visited the Xubuntu download-page, so I went to another website to get the cd-image of Xubuntu for PPC. I see what you mean about your experiences with Ubuntu & the computers, on which you run that operating system. Thanks for your help.

> **igknighted said:**
> It doesn't matter what distro you choose, all that matters is what software you run.  The software choices are the same either way.

I would choose yellow dog linux (ydl) for PPC computers, but that's just me.

Thanks. I'll use Yellow Dog Linux, as soon as necessary. I appreciate your help, as well.

> **Xiong Chiamiov said:**
> Neither.  Those are 32-bit and 64-bit Intel processor types.
Thanks for helping me. I see what you mean.

> **avtolle said:**
> @NewsAndHistory: try [http://cdimage.ubuntu.com/xubuntu/ports/releases/](http://cdimage.ubuntu.com/xubuntu/ports/releases/) for ppc releases of Xubuntu.
Thanks. I appreciate you. I will go to that webpage.

> **Frak said:**
> In my humble opinion, I'd rather use YDL on a G3 than Xubuntu. The difference in speed between the two is noticeable, and YDL is exclusively developed for PPC (G3, G4, G5 Mac) machines.
You've helped me. I appreciate you. I will get Yellow Dog Linux for my iBook.


> **mjheagle8 said:**
> i'd say yellow dog also. something designed exclusively for the hardware type you use is almost always faster, safer, and overall superior.
I see what you mean about all of that. Thanks for helping me. I appreciate you.

---

### Post by daniel-linux on 2009-04-11
*Please tell me which version of Xubuntu would work on an old iBook G3 (Processor: 600 MHz PowerPC)?*

The one for the PPC architecture.

*Is Xubuntu 8.10 (Intrepid) faster than 8.4.1 (Hardy Heron)?*

Yes. The core system is the same (well, different versions - 8.04 vs. 8.10), but the graphic user interfaces are different - Xubuntu uses Xfce, which is more lightweight (less RAM/CPU consuming) than Gnome (used by default in Ubuntu).

*Which of these versions works on PowerPC (PPC) computers: i686 or x86 (amd64)?*

i(3-4-5-6)86 or x86 is the same - 32 bit computing. amd64 stands for the x86-64 architecture. you will need the ppc version, as stated above. 

*I need an operating system that will work faster than Panther OS X 10.3.9. That's why I'm trying to find out whether Xubuntu or Fedora would run better on my old iBook.*

They will, but you have to install Xfce as a GUI. So for instance, if you install Fedora (which comes with Gnome or KDE by default), you will have to install Xfce afterwards, to save some RAM/CPU resources.

YDL is crap, IMHO. They SAY it is optimized for PPC and what not, but in practice it sucks, period. Stick with Fedora, Ubuntu, Debian or OpenSuSE. Those are ok for production. (You can use Xfce on top of Xorg on ANY of them.)

If you want to learn more about the system's internals, try Gentoo (even though compiling from source can be quite time consuming, so ONLY use this if you REALLY want to build your system from scratch; you will learn a lot along the way, they have a great online documentation).

---

### Post by Gen2ly on 2009-04-11
I haven't tried YDL but i've heard good things about them.  I think they do generally troubleshoot more errors for ppc than any other distro.  i don't think the install/upgrade experience is that great from what i've heard though.  For my ppc I've used Gentoo (for experienced ppl), Debian, and Arch.  They are all good.  For the new user of those i'd recommend Debian.  Ubuntu makes a PPC installCD too but it's based on Debian's and I think Debians gets a little better support.

---

