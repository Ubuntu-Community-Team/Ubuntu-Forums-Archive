---
title: "Old Laptop + Lucid wont boot--- Hangs"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2010-04-29
I have an old Compage Presario M2000 laptop that I have tried to load Lucid on.

The very first time I did it it installed and worked, except for the inbuilt wireless card which is a Broadcom that required the BC43 xx driver

Initially I got it to work and managed to get the wireless to work, then I did a package update and since then it refuses to boot. It gets to the first Ubuntu splash screen then hangs

So, I re-installed lucid from scratch...no luck

I installed Karmic...no luck..

I installed Lucid again...with a network connection....still no luck..

I am familiar with installing Ubuntu...have done it a few times on various machines, but this one wont seem to behave

I managed to get photo of the screen to see if anyone can help, it no the best pic, but gives some clue

---

### Post by Ducatiboy Stu on 2010-04-29
Ubuntu 7.10 and 8.10 liveCD both work and I can read the HDD, Is there a way to use the live CD to start up 10.04 off the HDD ...

---

### Post by acorreia on 2010-04-30
Did you try the solution on this post (#14 - Eureka)  ?

[http://ubuntuforums.org/showthread.php?t=1463294&page=2](http://ubuntuforums.org/showthread.php?t=1463294&page=2)

Hope it helps...

---

### Post by ugm6hr on 2010-05-01
That error looks like it is part way through trying to install b43 wifi driver.

Wipe the HD, then reinstall Lucid with no network connection.

Then you will have to manually reinstall b43 driver.

---

### Post by zeekoman on 2010-05-01
Yeah, I had the same problem with a computer of mine..

I think you should get rid of any OS on your system and install Lucid with a wired connection, if possible. From there your going to have to either use synaptic to find B43fwcutter and wget the driver.

Try this help article for instructions.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Ducatiboy Stu on 2010-05-03
I managed to use SuperGrub disk to boot into Lucid..

I think there is something to do with initramfs...

---

