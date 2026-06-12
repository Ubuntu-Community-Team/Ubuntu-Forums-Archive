---
title: "VBox operation assist?"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-05-11
Didn't find what I wanted so thought I'd ask in a different way and see what I get.

I installed the Sun VBox, and Windough$ XP, in hopes of ending the need to use dual boot. I have a few reasons for doing this: A Canon MP560 Printer at home, a Lexmark Z816 I use "on the road", a Magellan Explorist GPS and a couple of other things that the manufacturers don't speak Linux with.

I was hoping that I could "install" these devices in the XP in VBox but it appears that it must first be compatible with the Linux before you can do that. (I was hoping I'd be able to jump from 10.04 into XP when needed, get the task done, and jump back out. Not have to reboot, etc)

I read the Help with the VBox, but none of this appears to be addressed there.

Has anybody done this before and gotten things installed and working in VBox that don't work in Linux/Ubuntu? (Currently using 10.04) If so, could you provide me with the step-by-step to do it or, if not, know where I could find that info?

I don't plan on spending lots of money to get Linux compatible(s) so, if all else fails, I can just boot to Windough$ while doing shows and save the 10.04 for home use.

Thanks for any assist.](*,)

---

### Post by Ozymandias_117 on 2010-05-11
If the devices connect through USB, I think it may work. If not, I'm not aware of any way to make it work.

---

### Post by marshmallow1304 on 2010-05-11
You did get the [PUEL version]("http://www.virtualbox.org/wiki/Linux_Downloads"), right?  The version in the Ubuntu repositories does not support USB.

---

### Post by flyfishingphil on 2010-05-11
> **marshmallow1304 said:**
> You did get the [PUEL version]("http://www.virtualbox.org/wiki/Linux_Downloads"), right?  The version in the Ubuntu repositories does not support USB.
Good question. In viewing the info on the Sun version installed it reads: 3.1_3.1.8 r61349 and is from: [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid  non-free

In looking at your reference site it reads:virtualbox-3.1_3.1.8 61349~Ubuntu~Lucid.deb

So, I guess the big question is is it the same one, or is that little "r" in front of the Sun number standing for restricted?

What I did notice, when I plugged in the printer, was that it opened up the Ubuntu install process for a printer and pulled the mouse from the VBox to the Ubuntu side of operation. I then had to hit the Control (right) to put the mouse action back in the VBox/XP to do anything in VBox.

Would it be best to uninstall the Sun version I have and try the other one? Is it a simple uninstall, or are there numerous steps to removing the current version and everything else attached to it?

Confusing enough? I did notice when I unplugged the USB connection for the mini mouse, and moved it to a different port, VBox noticed the move. Also, Ubuntu responded whether the printer was plugged into the single USB port on the right or the dual on the left. Since Ubuntu responded immediatley I don't know if anything in VBox responded.

I did try to install the printer in XP, marked had cd, but it would not read the cd and said no drivers found. I went to Lexmark and downloaded the drivers, using XP in Vbox but could not locate that download when it was done.

&&5$@(&^$#^&*>:&$#@!!^&( (No problem for saying that "in code")

---

### Post by Ozymandias_117 on 2010-05-12
To move a USB device from Ubuntu to Virtualbox, you have to click on the little USB icon at the bottom right of the VBox and select the USB device you want it to be able to access.

---

### Post by flyfishingphil on 2010-05-12
I dug thru everything I can find and it appears to be that if it is not compatible with Ubuntu it is not usable in VBox either. Guess I'll just have to put up with the dual boot side. Didn't seem to matter what I tried it would not recognize the Lexmark printer or install the drivers for it. Now I just have to go thru and figure out how to get rid of any "junk" left behind and filling space.

Thanks for trying.

---

