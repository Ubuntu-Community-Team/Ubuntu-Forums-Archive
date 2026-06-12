---
title: "In need of super help"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by krisarnold on 2009-06-16
HELP!!! I' recently upgraded to jaunty. Been trying to get my graphics card to work, even for a few effects.  I entered   sudo dpkg-reconfigure -phigh xserver-xorg and restarted. It loads fine, but then It won't quite bring up the desktop. It tries like 3 times before it stops with some half burned in image of the load screen. PLEASE HELP!!! I am using a live 8.10 disk now. Any help would be greatly appreciated.

---

### Post by krisarnold on 2009-06-16
I keep trying and it keeps failing. I've even tried to restart from there. There is no screen or mouse or anything to see if it even responds. Just blurred load page. I really don't want to have to reload 8.10 and do the upgrade to 9.04 again....

---

### Post by LowSky on 2009-06-16
sounds like you keep loading the wrong informaion into xorg

go to recovery mode from Grub and choose XFIX

---

### Post by Amilo1718 on 2009-06-16
ATI, Nvidia or Intel?

---

### Post by krisarnold on 2009-06-16
I believe it is a ATI RADEON m6 or something, but I thought it was just an intel before. At this point as much as I would like to have any graphical effects, I just want it to start.

---

### Post by Bios Element on 2009-06-16
> **Amilo1718 said:**
> ATI, Nvidia or Intel?

[http://pcworld.about.com/news/Feb122002id83366.htm]("http://pcworld.about.com/news/Feb122002id83366.htm")

ATI according to that.

---

### Post by LewRockwell on 2009-06-16
You're not trying to load it onto your:

"Old Dell c610. P3 And a half a gig a RAM."

are you!?!?!?!

---

### Post by krisarnold on 2009-06-17
Yeah. I had it working with 8.10. I even upgraded to 9.04. Was more than fine. But no......I had to try to get my graphic effects working and now they are messed up. What is the command to have ubuntu discover its own settings?

---

### Post by lavinog on 2009-06-17
Your video card isn't supported by the proprietary driver anymore. Since you upgraded from intrepid, is it possible that you installed the proprietary driver in the past?
can you post your /etc/X11/xorg.conf

---

### Post by krisarnold on 2009-06-17
It never did find any drivers. After I installed Jaunty I kept messing with it and inputted the command that is in the first thread of this post. Then I restarted and this...

I know there has to be a way to have it restore itself thru the grub recovery. xfix or whatever doesn't do anything.

---

### Post by lavinog on 2009-06-17
Try removing compiz
```
sudo apt-get remove compiz
```

---

