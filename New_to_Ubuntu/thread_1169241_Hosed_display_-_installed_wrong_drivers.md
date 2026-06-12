---
title: "Hosed display - installed wrong drivers"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by malangbaba on 2009-05-25
So I had been having problems with videos.  My videos on fullscreen would appear a bit choppy.  This wasnt a problem in Intrepid, but only in Jaunty.

Anyway, I thought decided to install the ATI drivers - forgetting that my current laptop has an Intel card.  So now, I can see the Ubuntu logo/bootup screen, but get garbled lines when it reaches the desktop.

How do I fix this from Command Line?  I assume I need to remove ATI drivers, and reinstall Intel drivers.

I thought maybe I just needed to restore m backup xorg.conf, which I did, but that did not help...

NOTE: I am currently resorting back to Windows SO ITS URGENT!!!! :)

---

### Post by shifty_powers on 2009-05-25
you should be able to boot into the recovery console and use the xfix command iirc. (press escabe to get into the grub menu, go into recovery mode and it should be in the menu).

worth a try...

---

### Post by malangbaba on 2009-05-25
> **shifty_powers said:**
> you should be able to boot into the recovery console and use the xfix command iirc. (press escabe to get into the grub menu, go into recovery mode and it should be in the menu).

worth a try...

I did go into the recovery console, and did not see "xfix command iirc" as one of the options.  There was one option for "fix display problems" (or something to that effect, but that did not help....

Oh:
Jaunty Jackalope
Toshiba Satellite M105-S3041
Video: Intel 945GM Chipset

---

### Post by shifty_powers on 2009-05-25
hah, same graphics as me. and it's fecking crap.

btw, not sure how to solve the ati driver stuff, but when you do, [http://ubuntuforums.org/showthread.php?t=1130582&highlight=touchpad](http://ubuntuforums.org/showthread.php?t=1130582&highlight=touchpad) could be really useful :D

btw, do you have a separate home directory?

---

### Post by malangbaba on 2009-05-25
HEHHEY!

> sudo apt-get --purge remove xorg-driver-fglrx fglrx-control

sudo dpkg-reconfigure xserver-xorg

sudo apt-get install --reinstall libgl1-mesa-glx libglu1-mesa  libgl1-mesa-dri

That worked.  Thanks!

I'll look into the link you shared.

OH: Not sure what you mean by separate home directory.  But Ubuntu is all on one partition.  Why?

---

### Post by shifty_powers on 2009-05-25
serioulsy, if you are having probs with flash vidoes, that link si a life saver. oh and [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by malangbaba on 2009-05-25
Hey.  Did the safe option, and that made it much better. but still a bit choppy on fast paced videos....  Thanks!

Is it possible that any of the steps I took above could have affected my touchpad?...it seems not as smooth....

---

### Post by shifty_powers on 2009-05-25
yeah, the new uxa acceleration is still being developed but it is still a big improvement.

go system>preferences>mouse to check out the touchpad. it shouldn't have effected it, but may have reset some setting in there.

---

