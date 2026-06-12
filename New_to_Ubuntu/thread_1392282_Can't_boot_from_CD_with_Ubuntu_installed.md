---
title: "Can't boot from CD with Ubuntu installed"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by MikeinVA on 2010-01-27
I need a little help. My HD crashed and I installed a new 500GB and reinstalled XP (just to play a few games) and reinstalled Ubuntu 9.04 from my CD with the intent of upgrading (back) to 9.10. My partitions are so small I can't even do the first upgrade. So, I have been reading the posts and need to get the CD up and running so I can use GParted to increase my partitions. Problem: when I install the CD and restart the computer it just goes to the normal dual boot screen. What am I doing wrong? If I can't fix it how do I uninstall Ubuntu and start over? Thanks!

---

### Post by baltadt on 2010-01-27
It sounds like you need to change your BIOS setting so your computer boots from optical drive first.

---

### Post by rogue_0111 on 2010-01-27
Kinda off topic but next time use [virtualbox]("http://www.virtualbox.org/"). Less stress in your life.

Here's a how to video:

[http://tek-botics.webs.com/apps/videos/videos/show/6760140-how-to-get-virtualbox-on-windows](http://tek-botics.webs.com/apps/videos/videos/show/6760140-how-to-get-virtualbox-on-windows)

--

---

### Post by MikeinVA on 2010-01-27
Baltadt,
Thanks for the tip, but it does read from the CD first. That is why I can't figure out what is going on. It should just spin up the CD.

---

### Post by MikeinVA on 2010-01-29
Thanks for the help. I finally got it fixed. I had to go into Windows and delete the partitions, then run the live CD and shrink the Windows partition with GParted, then I had to load Ubuntu. Then after all the upgrades were done the sound wouldn't work, so I read the sticky on sound guide and got that fixed. This is a great forum!!!:popcorn:

---

