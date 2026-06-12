---
title: "ATI Radeon 9250 PCI card install"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by woodrow667 on 2011-02-05
Hi,

I have a Compaq Presario S6020WM desktop that I'm running xubuntu 10.10 on. I have an ATI Radeon PCI 9250 graphics card that I want to install in it. I have an onboard video card, but I want to use the ATI. I tried plugging it in and booting up, but instead of booting into ubuntu, it came up with a list of functions it was trying to do and then froze after running some kind of trace. I installed every ati package I could find in synaptic package manager, but it is a no go. Can anyone help me out?

Thanks,

Woody

---

### Post by cwsnyder on 2011-02-05
Did you first disable the on-board video before plugging in the new Video card?

---

### Post by woodrow667 on 2011-02-05
> **cwsnyder said:**
> Did you first disable the on-board video before plugging in the new Video card?

I did in bios. Do I need to do it in terminal? I don't know how to do that.

---

### Post by cwsnyder on 2011-02-05
No, I was referring to the BIOS setup.

Google-ing tells me that the ATI Radeon 9250 is old enough that it doesn't work with the *fglrx* restricted drivers.  Recommended is that you stick with the open source drivers for compiz.  Referenced thread: [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by wep940 on 2011-02-05
Yeah, I had an ATI 9250 Pro for a couple of years and late last year gave it to someone else.  The fglrx driver indeed doesn't work with the card, nor does any other driver from ATI that I could find.  I used what ever it came up with by default and it ran desktop effects fine.

---

### Post by woodrow667 on 2011-02-05
Thanks for the help. I tried the fix in the thread you posted, but it just didn't work for me. Thanks anyway.

---

### Post by wep940 on 2011-02-07
When I had the 9250 Pro, I didn't load any driver for it - I just let X figure it out, and it did as radeon (which the 9250 is).  The default that loaded that way worked great for desktop effects. etc.  If you have installed, or tried to install, other drivers, try removing them first, then reboot and see what X does for you.  You may need to adjust the resolution depending on whether or not your monitor is declaring itself.

---

### Post by gandaran on 2011-02-07
I installed an ATI Radeon 9250 PCI card (250MB) last week on this desktop and I didn't install or do anything, the card disabled the onboard SIS while booting the first time and I can say I'm quiet  impressed with the card, the desktop compiz effects are running very well with the default ubuntu drivers just like any other newer ati or nvidia with proprietary drivers! 
I don't know what causes your problem, maybe something to do with the BIOS but the drivers it isn't.

---

### Post by wep940 on 2011-02-07
Since you said you installed "every ATI package in Synaptic Package Manager", that's going to be part of your problem.  Via the package manager, remove all ATI packages except the default open driver.
 
I hate to say it, but you may have things at a state where it might be best to back everything up and reinstall from scratch with the ATI card in.  Mine was recognized by default even on new installation.

---

