---
title: "How do you add a different display option?"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by Bodhibear420 on 2009-11-13
Hello,
I'm a complete newbie to Ubuntu, and not the most computer savvy person to begin with, but here it goes.  I installed 9.10 on an optiplex gx280 with a 3.2 p4. I installed with wubi on a system with XP.   I am  using a Starlogic 20.1 monitor but the display setting reads as 19 inch.  I need to change the resolution to 1280x768 but it does not give that to me as an option.  How can I fix this situation.  Thank you

---

### Post by 0cton on 2009-11-13
are you sure you have that resolution let's in XP and it's functional?
You should know that every monitor can send to the OS the modes it supports and I doubt ubuntu got them wrong (possible nonetheless)
Also does it really seem to be of an issue to you?
I would recommend editing Xorg.conf in /etc/X11/ (you need root for that)

---

### Post by Hospadar on 2009-11-13
before you worry about xorg.conf,

what kind of video hardware do you have?  That probably has more to do with your problem then the monitor itself.

---

### Post by Bodhibear420 on 2009-11-13
That is the resolution I have set in XP and it works great.  The setting that it stars out with is HUGE and the closest one I can set is 1024x768 but it stretches everything from side to side.  The monitor is a widescreen if that helps at all.  As far as editing Xorg.conf in /etc/X11/, that is a foreign language to me so I'll need more explicit direction than that.  Sorry, when I say newbie I mean newbie.

---

### Post by Bodhibear420 on 2009-11-13
The video is just an integrated Intel Extreme Graphics.  With the small form factor, I can't put in a different video card.

---

### Post by Gaweph on 2009-11-13
Dont you need to install your graphics drivers before all of the resolutions become available?

What graphics card do you have.
If you go to:

SYSTEM -> ADMINISTRATION ->HARDWARE DRIVERS/RESTRICTED DRIVERS

is ther an option to tick there?

I think your problem is that in windows XP you ahve the driver and in ubuntu you havent installed it yet.

---

### Post by Bodhibear420 on 2009-11-13
When I do that, it says "no proprietary drivers are in use on this system".  So I'm thinking that is the issue.  so I guess I need to locate a driver or find the disc that came with the monitor, right?

---

### Post by durand on 2009-11-13
Have you tried changing the screen resolution in System > Preferences? I can't remember the name of the menu item..

---

### Post by Bodhibear420 on 2009-11-13
Durand, I tried in the System>preferences>display, but it doesn't give me an option for the resolution I need

---

### Post by durand on 2009-11-13
Oh. Try this in a terminal (Applications > Accessories > Terminal):

```
sudo dpkg-reconfigure xserver-xorg
```

> I was having a problem a a few months ago that sounds a lot like what you are dealing with (check out [http://www.linuxquestions.org/questi...d.php?t=465994](http://www.linuxquestions.org/questi...d.php?t=465994)). Basically, how I solved it was by running "sudo dpkg-reconfigure xserver-xorg" in the terminal, and going through the xserver reconfiguration. When I got to the part for selecting available resolutions, I only selected the one I wanted my screen to use. Once I rebooted, everything was working fine. I hope this helps, so be sure to tell me how it goes.

as posted here: [http://www.linuxquestions.org/questions/linux-hardware-18/stupid-intel-extreme-graphics-not-giving-me-full-resolution-479124/#post2403677](http://www.linuxquestions.org/questions/linux-hardware-18/stupid-intel-extreme-graphics-not-giving-me-full-resolution-479124/#post2403677)

---

### Post by Bodhibear420 on 2009-11-13
When I type that into the terminal, it doesn't do a thing.  It just pops up another line that has my name @ubuntu:~$

---

### Post by durand on 2009-11-13
Hmm, maybe things have changed since that was posted :S This thread seems to have a similar problem to you. Maybe you could collaborate?

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7956388](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7956388)

---

### Post by Bodhibear420 on 2009-11-13
ok, I think the issue is I need to download a driver for my intel 82915G/GV/910GL integrated video.  Can anyone please tell me how I do this?

---

