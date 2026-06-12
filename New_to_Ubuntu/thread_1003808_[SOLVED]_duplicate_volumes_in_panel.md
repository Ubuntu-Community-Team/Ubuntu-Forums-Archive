---
title: "[SOLVED] duplicate volumes in panel"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by adobrakic on 2008-12-06
I'm using Linux Mint 6 RC1 (based off of Ubuntu 8.10), and instead of showing volumes on the desktop, I have it so it shows it on my top panel.
It works fine, but it shows two of the same mounted device. For example, it shows my iPod twice and my Blackberry twice.

Is there a way I can fix this?

---

### Post by lovelyvik293 on 2008-12-06
Yes you can solve this problem by changing the /etc/fstab file.In this case there are two entries for a same drive in the fstab file.

---

### Post by Astenorh on 2008-12-06
are you using KDE or Gnome?

check also what you have in /media/* folder
to do so just type in the console

```
ls /media
```

while you have one of your devices mounted

---

### Post by adobrakic on 2008-12-06
> **lovelyvik293 said:**
> Yes you can solve this problem by changing the /etc/fstab file.In this case there are two entries for a same drive in the fstab file.

I just tried, and I'm too noobish to know what I'm doing with that. :lolflag:

> are you using KDE or Gnome?

I'm using Gnome

```

ado@ado-desktop ~ $ ls /media
ADO'S IPOD  cdrom  cdrom0  cdrom1  disk
ado@ado-desktop ~ $ 

```

---

### Post by adobrakic on 2008-12-07
bump

---

### Post by mgmiller on 2008-12-07
This happened to me once.  Somehow, the panel applet got installed 2 times. 
Mount something so the 2 instances show up.
Right click one of them and select "Remove From Panel".

Hopefully, one will disappear and one will remain.

Problem solved????

---

### Post by adobrakic on 2008-12-07
Ah, yeah that's exactly what happened haha.
How weird. :x

Thanks!

---

