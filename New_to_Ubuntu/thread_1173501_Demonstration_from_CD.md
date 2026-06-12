---
title: "Demonstration from CD"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by ibates on 2009-05-29
Now this really is a beginners question!

I have two Ubuntu 9.04 CD's; one from Canonical and the other from a download (Check Sum checks OK).

After booting on either CD, I have attempted to run a demonstration from the CD.  On all attempts from each disc, the screen shows "Loading please wait .... " and from that instant, the machine hangs, and the only thing that happens is the Caps Lock and Scroll Lock light flash continuously.

A reboot is the only way from there, and the whole cycle starts again.

This does not appear to be a very encouraging start to a new Ubuntu experience.

I am using an ASUS P5VD2-X MB, and a TSST DVD read/write drive as the boot drive.

What the heck ????

---

### Post by albinootje on 2009-05-29
> **ibates said:**
>  I am using an ASUS P5VD2-X MB, and a TSST DVD read/write drive as the boot drive.


Apparently earlier versions of Ubuntu worked :
[http://www.nvnews.net/vbulletin/showthread.php?t=90531](http://www.nvnews.net/vbulletin/showthread.php?t=90531)

Here's someone else with problems, a solution was found but not posted, perhaps you can PM that person :
[http://ubuntuforums.org/showthread.php?t=1098845](http://ubuntuforums.org/showthread.php?t=1098845)

Can you try different boot options, see here :
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by ibates on 2009-05-29
I have had a look at these possibilities, but none seem to address the real problem.

The system is booting from the Ubuntu CD just fine, but when selecting Demonstration .... the whole show hangs after the dialogue "Loading Please Wait".  It could be significant that this dialogue is presented with each letter "a"  in a different font to the rest of the phrase.

I am not about to go and install Ubuntu if I can't even get the demonstration program running after it boots from the Ubuntu CD.

Anyone with any further thoughts.

---

### Post by ibates on 2009-05-31
Problem solved.  Selected ACPI=off.  Everything now works OK.

Thanks anyway.

---

