---
title: "Is My Graphics card supported?"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by daj_uk on 2010-03-09
Hi All

This is my first serious step into the Linux community. 

I've dabbled with various Linux distros. in the past but always struggled with the command line requirements.  I have now given this another attempt with the latest Ubuntu and I LOVE IT.  I managed to install it without issue on a laptop and a PC.  I even added extra software!!

What I want to do now is install it on my main PC however when I tried it failed -- it looks like it has a problem with my graphics card as nothing displays on the screen just after the GUI install starts.

I have read a little on this and it is suggested I use the Alternative Text based installer.  My worry is that even after the install is successful, Ubuntu will still not work with my graphics card.   Is there any way to check?

My setup:

HP PC with Intel Core 2 Duo, 3Gb ram
Two HP L1906 LCD Monitors (so dual screen setup)
Nvidia GeForce 7300 


I use the Nvidia card to run the two monitors.  If I disconnect the monitors and plug one into the in-built graphics card, Ubuntu will start the installer so I know it is something to do with using the Nvidia card

Any help much appreciate for a newbie.

many thanks

---

### Post by bruno9779 on 2010-03-09
I'd say, go ahead with the install with the in-built graphics card, and when you are up and running, post back.

Nvidia support is pretty good nowadays, but still mostly proprietary: some of the required steps to get the best Nvidia support available, need your system to be already set up.

---

### Post by cascade9 on 2010-03-09
If you still have the onboard video card turned on in BIOS, its probably just that ubuntu is using that not the nvidia card. That card should work fine with the free 'nv' driver (but it will run better with the nvidia drivers)

I'd try turning the onboard card off in BIOS, if you can.

---

### Post by Simian Man on 2010-03-09
I'm surprised that your Nvidia card is not supported out of the box, usually they work with all drivers under Linux.

Anyway, by default Ubuntu comes with the open source "nv" drivers.  Once you have it installed, however, you can install the proprietary drivers from Nvidia which will almost certainly support your card, including the dual-monitors.

---

### Post by audiomick on 2010-03-09
Hi.
Have a look here
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)
as far as I can tell, your card is at least claimed to be supported.

First thing would be to boot into the "try without changing" option off the live CD (not the alt.CD). If that runs ok, your chances are good. If it doesn't, you should still be able to install from the alt.CD, but will probably have to buggerise around to get the GUI/Graphics working right.

---

### Post by patchwork on 2010-03-09
If the live cd is not able to configure your x server correctly with the two screens, there is a good chance it will take some manual configuration to make the screens work.  The card itself is supported (through both the opensource nv and proprietary nvidia drivers).

This shouldn't deter you, however, if you're comfortable with editing the configuration files (with the help of the forum).

---

### Post by daj_uk on 2010-03-09
thanks for all the suggestions.  I can not see any way to disbale the onboard graphics card in my Bios.

What I might do is install Ubuntu using the on-board video and once up and running try to get the Nvidia card going with some help from the forum ;)

Thanks for the quick replies and the reassurance that I should be ok to try this.

---

### Post by patchwork on 2010-03-09
Have you tried using the nvidia card with only one monitor?   If this works, it may save you some hassle in the long run.

---

### Post by daj_uk on 2010-03-09
> **patchwork said:**
> Have you tried using the nvidia card with only one monitor?   If this works, it may save you some hassle in the long run.

Good idea -- let me try booting Live CD just now, with one monitor

---

### Post by daj_uk on 2010-03-09
I have just unplugged one monitor from the Nvidia card and the Live CD actually worked  :D  I got all the way to the Desktop.

Even more impressive was the fact that Ubuntu popped up a nice helpful message suggesting I switch to a new graphics driver -- it suggested an Nvidia one; it did note that this was not 'open' (sorry forget the actual wording) but I could still download and install it.

All very promising and exciting

---

### Post by patchwork on 2010-03-09
How is the resolution?  Are you getting the desired 1280x1024 or is it in low graphics (800x600)?

If the resolution is setting properly, that's even less to worry about.

---

### Post by audiomick on 2010-03-09
That all sound good. As a tip, I don't think I got my dual monitors working until after the nVidia driver was installed.
when you get it installed, you have to start the settings thing with
```
gksu nvidia-settings
``` from the terminal, i.e. with root privileges (gksu), or it can't save the changes that it makes.

---

### Post by daj_uk on 2010-03-09
> **patchwork said:**
> How is the resolution?  Are you getting the desired 1280x1024 or is it in low graphics (800x600)?

If the resolution is setting properly, that's even less to worry about.
yes, I get the 1280x1024

---

### Post by daj_uk on 2010-03-09
> **audiomick said:**
> That all sound good. As a tip, I don't think I got my dual monitors working until after the nVidia driver was installed.
when you get it installed, you have to start the settings thing with
```
gksu nvidia-settings
``` from the terminal, i.e. with root privileges (gksu), or it can't save the changes that it makes.

Thanks for the tip

---

