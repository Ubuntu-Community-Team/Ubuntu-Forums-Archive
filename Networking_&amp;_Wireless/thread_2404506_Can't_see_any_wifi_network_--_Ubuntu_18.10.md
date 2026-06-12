---
title: "Can't see any wifi network -- Ubuntu 18.10"
date: 2018-10-24
forum: Networking &amp; Wireless
---

### Post by valuat on 2018-10-24
Hi, just upgraded to 18.10 in order to try and get my wifi working again. I was using 18.04 and everything was fine. After rebooting because of an update that came out yesterday/today I couldn't see any wifi network anymore.

Laptop is a DELL E6420 with the Broadcom BCM43228 STA driver. Here's my wireless-info.txt: [http://paste.ubuntu.com/p/J2PbNjDrhX/](http://paste.ubuntu.com/p/J2PbNjDrhX/)

---

### Post by valuat on 2018-10-24
Anyone? I really need it to work...

Thanks in advance!

---

### Post by wildmanne39 on 2018-10-24
Please be patient we are all volunteers here from all around the world so it is likely that the person that can help you has not seen your thread yet, if you do not get help you can bump your thread once every twelve hours.

Thanks

---

### Post by valuat on 2018-10-24
Sure, absolutely. Didn't know about the 12-hour rule. Thanks!

---

### Post by newagelink on 2018-10-25
It's not a '12-hour rule'; it's the nature of forums: Threads are traditionally listed by activity, e.g. at [this board's thread list]("https://ubuntuforums.org/forumdisplay.php?f=336"), and posting again to "bring it back to the top" only makes sense after it's fallen off the first page of that listing: As you can see there, the last thread listed there had activity a day ago. So you can probably wait an entire day before needing to post again to 'bring up your post'.

Have you tried [this answer]("https://askubuntu.com/a/60395/761477")?

It worked for my Broadcom BCM4311 driver in Lubuntu 18.10:

sudo apt install firmware-b43-installer

sudo reboot

---

### Post by valuat on 2018-10-25
PCI.ID = 14e4:4359; it seems I'm using the right driver (bcmwl-kernel-source).

Moreover, hardware is fine; everything works with a Windows live installation.

Wifi was working fine until some update that messed the whole thing up. I was hoping something could figure out what is going from the wireless-network.txt file.

---

