---
title: "/home in an  sd card"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by migrate from windows on 2011-03-12
Hi I have been using ubuntu 10.10 in my desktop, everything is fine I hardly use xp anymore. 
Now I want to install ubuntu in my laptop, I want to choose my sd card as the home directory during  installation is it possible? if so how?

---

### Post by migrate from windows on 2011-03-13
bump!

---

### Post by Hedgehog1 on 2011-03-14
migrate from windows,

This is possible (assuming the SD hardware and Ubuntu are happy to work together).

You can set if up at install time, or move '/home' afterwards.

In the first picture in the folloeing link, you will see what the **etc/fstab** file would look like:

[http://ubuntuforums.org/showthread.php?t=1705788]("http://ubuntuforums.org/showthread.php?t=1705788")

It is possible to combine many hard drivers into a single 'file system'.

***The Hedge***

:KS

**p.s. If you are going to do a 'full install' of Ubuntu on the laptop, save off any data you care about and practice installing and removing and reinstalling Ubuntu.  This is a great time to learn that...**

Here is someone who moved '/home' to and SD card later: [http://ubuntuforums.org/showthread.php?t=1703702]("http://ubuntuforums.org/showthread.php?t=1703702")

---

### Post by migrate from windows on 2011-03-14
Thank you very much! but since Im going to do a fresh installation at which point during the installation I should choose the SD card as /home?

---

### Post by Hedgehog1 on 2011-03-14
Yes, I think it would be best to do it as part of the original install; it will be good practice and then you can show others how to do it once you have the steps down.

You can install, and reinstall until you are happy with it.

***The Hedge***

:KS

---

### Post by wojox on 2011-03-14
> **migrate from windows said:**
> Thank you very much! but since Im going to do a fresh installation at which point during the installation I should choose the SD card as /home?

When you get to the "partition layout " screen, choose manual and it may allow you there.

---

### Post by migrate from windows on 2011-03-15
Thanks wojox.

---

