---
title: "Live CD and Video Card Driver"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by gustavo.glenmorangie on 2009-04-09
Absolutely new here.

I'm trying to run Ubuntu from the CD to get myself started. 

I have an ATI Radeon HD 2400 Pro video card installed. When I boot up Ubuntu, I get nothing on the screen. Seems obvious that the video driver is not installed.

I can run from the CD if I use the VGA video from the mother board, but the Dell Optiplex755 will only boot that way if I pull the video card out. That, needless to say, is a major PITA.

So, question number one: Is there a way to get the driver loaded when booting from the CD.

Question number 2: Assuming the answer to number 1 is "no", how do I load the driver if I install an ubuntu partition.

thanks

gustavo glenmorangie

---

### Post by Hospadar on 2009-04-09
Just to clarify: you cannot boot into a graphical environment from the livecd with the video card plugged in?

Also, when you boot into recovery mode (from the grub menu, not off your livecd, but off your installation) do you notice any video-related error messages?

You might want to just try a jaunty cd (there's a link on the ubuntu homepage), it's coming out in a matter of days anywho, and oftentimes hardware issues are solved in major release cycles.

---

### Post by Bakon Jarser on 2009-04-09
Yeah, I would probably try jaunty if I were you.  But there is a way to install to a partition without loading a video driver.  You would need to use the alternate cd.  I've never done it before so can't give you more info than that.  Good luck.

---

### Post by Therion on 2009-04-09
Step one would be to boot into your system BIOS and disable the on-board graphics chip-set since you've installed a discrete graphics card (the ATI HD 2400).  You want your system to have ONE clearly defined output path in the hardware profile; currently you have two.  

All that being said, this may, or may not, solve your problem, but even if it doesn't it's Standard Operating Procedure to disable on-board chip-sets when installing discrete solutions.

---

### Post by gustavo.glenmorangie on 2009-04-09
The on-board output is disabled when the ati card is in place. That is why I have to remove the ATI card to get it to boot with the on-board card active.

I'll look for jaunty and see what happens.

---

