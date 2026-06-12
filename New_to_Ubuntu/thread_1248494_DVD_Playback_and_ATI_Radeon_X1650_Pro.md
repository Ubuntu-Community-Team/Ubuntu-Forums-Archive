---
title: "DVD Playback and ATI Radeon X1650 Pro"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by KyleRickards on 2009-08-24
Hi all

Hoping someone can help.

Have enabled restricted packages and installed VLC. For a few days everything was good, but now my system completely locks when I attempt to watch DVDs and I need to hard reset. My graphics card is **[B]ATI Radeon X1650 Pro.** 

[/B]No alternative drives are suggested in the hardware drivers section. Is there anything I can do without having to reinstall everything?

Thanks
Kyle

---

### Post by halitech on 2009-08-24
> **KyleRickards said:**
> Hi all

Hoping someone can help.

Have enabled restricted packages and installed VLC. For a few days everything was good, but now my system completely locks when I attempt to watch DVDs and I need to hard reset. My graphics card is **[B]ATI Radeon X1650 Pro.** 

[/B]No alternative drives are suggested in the hardware drivers section. Is there anything I can do without having to reinstall everything?

Thanks
Kyle

Don't watch DVD's on the computer? ;)

you don't mention what version you are using or if you have compiz enabled. If you are using 9.04 then I don't believe there are any drivers to install (ATI dropped support for the x1650 as of Catalyst 9.3) but the open source drivers may work (ignore if you have 8.10 or lower)

If you have Compiz enabled, try disabling it and playing a movie again and see if it still locks up

---

### Post by KyleRickards on 2009-08-24
Thanks Halitech.

Two things, how do I disable compiz? Also, I swapped the graphics card for my old one and am now stuck in Initramfs mode/busybox and cannot load up - do I have to reinstall? :(

Kyle

---

### Post by halitech on 2009-08-24
I think its under System - Preferences - visual effects. Set it to none

try
```
dpkg-reconfigure xserver-xorg
``` to configure x again. if that doesn't work you may have to manually edit xorg

---

### Post by KyleRickards on 2009-08-24
Sorry, do I load from Live CD to do this, not sure how to edit it - am stuck in initramfs...

---

### Post by tuxxy on 2009-08-24
I had trouble with that card, you say it wont run DVD well when I had one it wouldnt even run a single thing.  I upgraded from that card to nvidia cards and I have never looked back :D

---

### Post by KyleRickards on 2009-08-24
Thanks Tuxy, think I will swap it - at the moment, I would settle for getting back into my system :(

---

### Post by tuxxy on 2009-08-24
I understand that, did you try the suggestion to run 

```
dpkg-reconfigure xserver-xorg
```

If you cant get to a command line then your other option is to boot the Ubuntu CD and select recovery mode, then choose the xfix option which will run the command above :D

---

### Post by KyleRickards on 2009-08-24
Loaded up with pendrive and selected compatibility mode which got me in, ran the command, which asked lots of things about keyboard and then nothing? Will try the CD now... Sorry

EDIT - in recovery mode now, still putting me into busybox - should I just reinstall?

---

### Post by tuxxy on 2009-08-24
If your in a terminal run the command above which will ask you a series of questions and then should restart with default graphics.

---

### Post by RomeReactor on 2009-08-24
Hi Kyle. Can you give us more details about your system (RAM, CPU, Ubuntu version)? The x1650 pro (I have one too) is perfectly capable of playing back DVDs and even 720p HD videos, even with the open source driver, so the problem might be elsewhere. A thing to have in mind, though, is that this card is overheats a lot and is very prone to it. Make sure the fan still works, that it's free of dust, and that it's correctly seated in it's slot.

Also once you're in recovery mode, select XFIX to try and correct your display.

---

### Post by KyleRickards on 2009-08-24
Hi

If I pick recovery from my default installation, I get the busybox screen. If I load from CD I am unsure how to get into recovery mode but can get terminal. The error I am getting is "/dev/sdd1 does not exist. Dropping to shell" so I think it's less graphics than drive issue? (even though I didn't alter that)

---

### Post by RomeReactor on 2009-08-24
Which video card do you have in your system now? If it's the nVidia, try putting the x1650 back in and see if you still get the error.

---

### Post by KyleRickards on 2009-08-24
Hi all

Sorry about this :(

I think the graphics card is an overheating issue but will fix that later!

If I get into recovery mode I can see a line pointing root to sdd1 I think, this is causing the error, is there anything I can change that to?

EDIT- Interestingly when in Live mode off CD, I can see all my drives apart from the one where Ubuntu is installed. Will load back into windows and see if the drive has failed maybe?

---

### Post by RomeReactor on 2009-08-24
You can check in **/etc/fstab** to see if root still points where it should:
```
cat /etc/fstab
```

Note that if you're using the live cd you need to look up the file in the HD, otherwise it will show you the one from the live cd.

---

### Post by KyleRickards on 2009-08-24
Well looks like the IDE cable to drive was faulty so it wasn't picking it up. Swapping everything round then will go in through Live CD and make sure it sees the correct root drive now.  Thanks one and all.

And when I finally get back in I will order a new graphics card - probably nVidia!!

---

