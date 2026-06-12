---
title: "How do I increase the  size of my Ubuntu partition?"
date: 2010-12-29
forum: New to Ubuntu
---

### Post by rom3lol on 2010-12-29
I am running windows 7 and ubuntu and I would like to add more hdd space to Ubuntu.
Is this possible?
I happen too like Ubuntu very much now and im planning to leave windows in the dust):P

---

### Post by davidmohammed on 2010-12-29
how have you installed ubuntu - using wubi or as a proper dual boot?

---

### Post by Don1500 on 2010-12-29
> **rom3lol said:**
> I am running windows 7 and ubuntu and I would like to add more hdd space to Ubuntu.
Is this possible?
I happen too like Ubuntu very much now and im planning to leave windows in the dust):P

 The best way would be to go to the  ([[COLOR="Blue"]G-Parted download page[/COLOR]]("http://gparted.sourceforge.net/download.php")) and make a disk for yourself (Same way you made the Ubuntu disk using an ISO file). Boot from that disk and you have access to all your hard drives and partitions, nothing is mounted.

---

### Post by rom3lol on 2010-12-29
> **Don1500 said:**
> The best way would be to go to the  ([[COLOR=Blue]G-Parted download page[/COLOR]]("http://gparted.sourceforge.net/download.php")) and make a disk for yourself (Same way you made the Ubuntu disk using an ISO file). Boot from that disk and you have access to all your hard drives and partitions, nothing is mounted.

So with this program I cant use it too boot into the system and edit the hdd partition without damaging anything?
At least that's what the website said.

> **davidmohammed said:**
> how have you installed ubuntu - using wubi or as a proper dual boot?

I installed it as a proper dual. ? 
I resized windows and installed ubuntu

---

### Post by IWantFroyo on 2010-12-29
In GParted:
What you do is you find your windows partition, right click-resize/move and make it a smaller with the slider thingy. Then you go to your ubuntu partition, and right click-resize/move, and notice the empty space before the slider. Move the slider all the way to the right, and you're done!!!

---

### Post by rom3lol on 2011-01-21
> **IWantFroyo said:**
> In GParted:
What you do is you find your windows partition, right click-resize/move and make it a smaller with the slider thingy. Then you go to your ubuntu partition, and right click-resize/move, and notice the empty space before the slider. Move the slider all the way to the right, and you're done!!!

Very Simply Thank Froyo !

---

