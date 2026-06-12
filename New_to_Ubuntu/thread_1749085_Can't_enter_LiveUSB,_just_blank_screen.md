---
title: "Can't enter LiveUSB, just blank screen"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by faizalnex on 2011-05-04
Heeeelp T_T
I just cant enter my live 11.04 live usb. After loading, just purple blank screen.
Exactly doesnt enter the home screen.
Specs :
AMD X2 P360 2.3 GHz
ATI Mobility 4250
2 GB RAM
Ubuntu 11.04 64bit
Have previously installed Windows 7 64 bit.
Help please..
I miss my ubuntu..:confused:

---

### Post by ohadcn on 2011-05-04
how have you made this usb?
did this usb worked for you any time?
remember that just copying the files into the usb is not enough, you need to use a tool that can copy a boot sector into the usb.

---

### Post by I2k4 on 2011-05-04
I won't even ask what you did.  Just do this step by step, perfectly illustrated "Show Me How" that Ubuntu offers:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Be sure to permit formatting the disk to wipe out whatever you've done.

Personally, I go further at Step 2, and add Persistence to the Live USB on the excellent recommended installer.  For 11.04, I'd suggest 2GB for the operating system and set the remainder of your USB drive for Persistence.

(I've tried 11.04, worked perfectly, but am not wild about it for my purposes.)

---

### Post by faizalnex on 2011-05-07
I've just made the live usb like i was did on my ubuntu 10.
The live usb is working on my PC but not in my laptop.
I dont know why?
anybody?

---

### Post by wilee-nilee on 2011-05-07
> **faizalnex said:**
> I've just made the live usb like i was did on my ubuntu 10.
The live usb is working on my PC but not in my laptop.
I dont know why?
anybody?

Hold down the shift at powering on at the choice of install or try ubuntu, check memory...etc, hit the f6 key mark the nomodeset and boot in from there.

This is a low graphics boot if you get in you may need to run a low graphics boot to get to the installed Ubuntu if you install

To do this you choose the recovery 2nd partition (grub menu), then failsafe boot, login at the gui and run  startx to get to the desktop.

---

### Post by faizalnex on 2011-05-08
> **wilee-nilee said:**
> Hold down the shift at powering on at the choice of install or try ubuntu, check memory...etc, hit the f6 key mark the nomodeset and boot in from there.

This is a low graphics boot if you get in you may need to run a low graphics boot to get to the installed Ubuntu if you install

To do this you choose the recovery 2nd partition (grub menu), then failsafe boot, login at the gui and run  startx to get to the desktop.
i've tried that (f6 and nomodeset)
just same as before.
After booting up (ubuntu logo with purple screen) it doesnt enter the main ubuntu.
Just purple screen and often just black screen. And it doesnt respond with any keyboard hotkey (ctrlaltdel etc)
I've try to wait it for about one hour and still no reacts.
And maybe it has a problem with the vga?

---

### Post by diablo75 on 2011-05-08
Maybe there's some sort of kernel panic happening that's locking the system up at boot.  I have an external sound card that connects via USB to my computer (it's actually a Line6 Studio GX guitar pre-amp I use in Windows, and before 11.04 came out, Ubuntu booted with it connected no problem.  Now it consistently causes a panic if it's plugged in at boot).

You may just have to wait for 11.04.1

I'm assuming you were just wanting to try Ubuntu 11.04 for fun but if you were intending to install, have you tried booting from a 11.04 Alternate ISO instead?  Or if you need a live environment to work in, have you tried booting from a 10.10 Live ISO?

---

### Post by faizalnex on 2011-05-08
> **diablo75 said:**
> Maybe there's some sort of kernel panic happening that's locking the system up at boot.  I have an external sound card that connects via USB to my computer (it's actually a Line6 Studio GX guitar pre-amp I use in Windows, and before 11.04 came out, Ubuntu booted with it connected no problem.  Now it consistently causes a panic if it's plugged in at boot).

You may just have to wait for 11.04.1

I'm assuming you were just wanting to try Ubuntu 11.04 for fun but if you were intending to install, have you tried booting from a 11.04 Alternate ISO instead?  Or if you need a live environment to work in, have you tried booting from a 10.10 Live ISO?
hmmm...
What do you mean 'to try booting from a 11.04 Alternate ISO instead'?
I've use ubuntu 10.10 before and the ISO/live and the installed one. They're works well until now.
But now i'm stuck in this 11.04 version.

---

### Post by CaptainMark on 2011-05-08
op has an ati gpu, i had a problem once where i couldnt even use open source drivers with an ati card, is there a way to help the op install in safe graphics mode and add the correct drivers manually before switching to normal graphics, this is what i had to do before but it was easier on a desktop because i could use the mobos graphics, will the alternate install do this

---

### Post by faizalnex on 2011-05-08
If my laptop can use another graphics, i'll do that...

---

### Post by diablo75 on 2011-05-08
> **faizalnex said:**
> hmmm...
What do you mean 'to try booting from a 11.04 Alternate ISO instead'?
I've use ubuntu 10.10 before and the ISO/live and the installed one. They're works well until now.
But now i'm stuck in this 11.04 version.

The "Alternate CD" is available here:

[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

This is a text-based install-only version of Ubuntu.  You can try to use this to install a fresh copy of Ubuntu.  If you have the Internet connected during install it should download some updates along the way, which may afford you a stable environment when the install is complete.  And just so you know, this text environment only comes up during the Install.  After installing, it will attempt to boot into the GUI as usual.

---

### Post by faizalnex on 2011-05-08
Thank's before.
I'll download and try that..

---

### Post by faizalnex on 2011-05-11
Yeah...
It can be installed. But the touchpad won't work..
Any solutions????

---

