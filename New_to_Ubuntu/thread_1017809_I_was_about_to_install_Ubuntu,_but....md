---
title: "I was about to install Ubuntu, but..."
date: 2008-12-21
forum: New to Ubuntu
---

### Post by Jerriy on 2008-12-21
[INDENT]... before that I was checking it all out with the Ubuntu Live-CD (dvd in my case) I downburned.

Here is my "issue" (I'm not even sure it is a "problem" ;>)
I have a widescreen monitor but the live-cd automatically loads up in 800x600 screen resolution. I then went to the "hardware drivers" menu-option and gladly a ubuntu-customized Nvidia driver was simply waiting for me to "activate" it. I did that but since the new resolution setup only goes into effect when the computer is rebooted, I am unable to see the new result (everytime I start ubuntu from the live-DVD it goes back to square one (i.e. 800x600)[/INDENT]

---

### Post by Skripka on 2008-12-21
> **Jerriy said:**
> [INDENT]... before that I was checking it all out with the Ubuntu Live-CD (dvd in my case) I downburned.

Here is my "issue" (I'm not even sure it is a "problem" ;>)
I have a widescreen monitor but the live-cd automatically loads up in 800x600 screen resolution. I then went to the "hardware drivers" menu-option and gladly a ubuntu-customized Nvidia driver was simply waiting for me to "activate" it. I did that but since the new resolution setup only goes into effect when the computer is rebooted, I am unable to see the new result (everytime I start ubuntu from the live-DVD it goes back to square one (i.e. 800x600)[/INDENT]

The LiveCD loads the entire OS into RAM (and/or swap space) and therefore resets at boot-no changes are kept on the drive.


The driver should work fine after install of *buntu and driver activation....BUT-*buntu must be installed first.

---

### Post by gettinoriginal on 2008-12-21
But the main point is that you know if and when you do install, the driver is there to use so that you will get proper resolution.  It is true that any changes made using the Live DVD cannot be saved, but the idea behind checking out Ubuntu first is to check:
1. Your hardware and Ubuntu are compatible
2. Your interaction with the OS
3. Your interest in continuing with an install
4. All the things you get are FREE   :P
5. Your chance to check with us here at Ubuntu Forums and see how excited we are to have you and help when needed.

---

### Post by Jerriy on 2008-12-21
> **Skripka said:**
> The LiveCD loads the entire OS into RAM (and/or swap space) and therefore resets at boot-no changes are kept on the drive.


The driver should work fine after install of *buntu and driver activation....BUT-*buntu must be installed first.I was thinking of that (while at the same time sneakingly hoping that there was some way to activate the video driver straight from the live DVD :)

---

### Post by baruch60610 on 2008-12-21
Even though the driver exists, I would still hesitate before installing Ubuntu for real.  I would try to find out whether other people using your video card (preferrably, using your whole setup) were able to get the resolution working correctly.

You might try Googling for "linux card-name" or "linux system-name" (where 'card-name' or 'system-name' are what card or system you have, of course) just to see whether others were successful in installing Linux and getting the right screen resolution.

I say this because I had serious problems with Intrepid and resolution, so much so that I eventually had to reinstall Hardy.  Since Hardy worked, I had no reason to suspect Intrepid might not.  In this case, it didn't.

---

### Post by Captain_tux on 2008-12-21
Lest we forget **ROM** = Read Only Memory.

---

### Post by teh_yodeler on 2008-12-21
Ok, load the live CD, "activate" the driver, and then press Ctrl+Alt+Backspace.  Tap it twice if that doesn't work.  It should restart the X environment and your resolution issues should be solved.

Or am I wrong?  Can you just log out and then log back in?  But try the Ctrl_alt_backspace thing.

---

### Post by albinootje on 2008-12-21
> **Jerriy said:**
> I was thinking of that (while at the same time sneakingly hoping that there was some way to activate the video driver straight from the live DVD :)

It is "normal" that all changes are gone after having used the live CD.

Doing
```

modprobe nvidia

```
and then indeed ctl-alt-backspace might make it work.

---

### Post by jimmy the saint on 2008-12-21
How about this.  What Nvidia card is in your computer?  If we know that, we can tell you if it is compatible

---

