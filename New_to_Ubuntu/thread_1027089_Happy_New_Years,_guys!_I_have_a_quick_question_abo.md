---
title: "Happy New Years, guys! I have a quick question about .iso images."
date: 2008-12-31
forum: New to Ubuntu
---

### Post by Obero on 2008-12-31
So I downloaded the Xubuntu 8.10 .iso file from the official Xubuntu website. I have a blank CD-R disc on my table. I'd like to burn the .iso file onto the disc so I can do an install of Xubuntu tomorrow. How do I do it? I'm on Ubuntu 8.10 right now, so if there's any available software already please direct me how to get the .iso onto the disc.

Thanks in advance, and have a good night. :)

---

### Post by abn91c on 2008-12-31
cant remember gnomes program but I use**[COLOR="Red"] k3b [/COLOR]**in kubuntu and it works great. you can use it in ubuntu also, its in synaptic

---

### Post by mikewhatever on 2008-12-31
Right click on the .iso file and select Write to disk.

---

### Post by Dr Small on 2008-12-31
I found the simplest way to do it is:
```
wodim -v dev=/dev/cdrom isoimage.iso
```

Works lovely for me :)

---

### Post by 5BallJuggler on 2008-12-31
I use gnome-baker

---

### Post by Paqman on 2008-12-31
Open up Brasero and click on "Burn image", make sure you wind the speed down nice and slow.

However, did you know you don't have to reinstall to use Xubuntu? If you install the meta-package xubuntu-desktop you can use Xubuntu on your current system, just pick whether you want XFCE or Gnome when you log in.

[More info here]("http://www.psychocats.net/ubuntu/xfce").

---

### Post by Keen101 on 2008-12-31
[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by LowSky on 2008-12-31
> **mikewhatever said:**
> Right click on the .iso file and select Write to disk.

+1 This works for me

---

### Post by Frak on 2008-12-31
Right click -> write to disk

---

