---
title: "Ubuntu Intrepid: Can Not Start the X Server"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by Kevide on 2009-03-10
Hello, I've read threads with similar issues, but as yet, they've not solved my issue.

I've booted into recovery mode and selected the repair x server issue, but upon boot the problem is still present.

Any advice would be appreciated.

---

### Post by Zogh on 2009-03-10
In my case it had something to do with me not removing the driver completely. I have no idea if you have ati or nvidia graphics. (you didn't provide much info) My problem was that my ati drivers took away my GUI after enabling ati's fglrx drivers.

If **the ati drivers are your problem** this might work.
If this is not your problem I have no clue, I've only been a ubuntu user for a couple of hours :D


sudo apt-get remove xorg-driver-fglrx fglrx-kernel-source
sudo dpkg-reconfigure -phigh xserver-xorg

...reboot

enjoy the crappy vesa driver.. 

I'm not sure we've got the same issue but it's worth a try.
I hope this will give you the GUI back

/Z

---

### Post by Kevide on 2009-03-10
Ah, apologies.

I'm using a Gateway 7324GZ laptop, built in 2005. Can't recall the graphics card, and it's on my belarc summary.

---

### Post by Kevide on 2009-03-12
*obnoxious bump*

---

