---
title: "gparted issue"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by jsf_pp on 2008-12-12
hi, i had i big issue with CCSM which ended up with a PSOD (purple screen of dead). i tried to uninstall ccsm from terminal, from the live cd, and... well, lets say now its worse.

so im trying to format and install again ibex, but this time i want to make a partition for ubuntu instead of using all disk with it.

thing is that, when i tried to format (from a cd live) with gparted i couldnt change from extended to fat 32 (to install ubuntu using wubi this time.).

[IMG]http://i38.tinypic.com/2elqgkn.png[/IMG]

why i cant now?
im sure i did this from gutsy last week?
its sth that ibex changed?

thanks!

---

### Post by earthpigg on 2008-12-12
sooo you want to install windows and then install ubuntu via wubi?

the first step, in this case, would probably be the windows install discs ;)

---

### Post by jsf_pp on 2008-12-12
really? just like that?
ok. i'll try, but i think its not posible if you have a partition which is not fat 32 or 16.

now, i dont know much anout this, maybe im wrong. thats why im askin actually, i know **** about computers :lolflag:, im just starting to learn.

---

### Post by earthpigg on 2008-12-12
yup, wubi requires windows to work ;)

do a standard normal every day windows install (i think windows xp/vista install will reformat whatever partition you choose to NTFS... **not** fat 32), **then** install ubuntu via wubi.


EDIT:
> 
so im trying to format and install again ibex, but this time i want to make a partition for ubuntu instead of using all disk with it.

my bad, misinformation on my part. wubi is **not** for partitions.... wubi is for, specifically, if you do **not** want to give ubuntu its own partition.

---

### Post by Duck2006 on 2008-12-12
Some info on gparted.

[http://wiki.partedmagic.com/index.php/Using_GParted](http://wiki.partedmagic.com/index.php/Using_GParted)

If you want to install ubuntu with Wubi.

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by earthpigg on 2008-12-12
what (i think) you want is a standard dual boot configuration?

1. install windows.
2. put ubuntu cd in, restart.
3. pay attention during the ubuntu install, the installer will help you partition.

:)

---

### Post by albinootje on 2008-12-12
Looking at your screenshot of gparted it shows a key-pair.
What happens when you double-click on it, or try right-click ?
Does it show an error-message ?

---

### Post by jsf_pp on 2008-12-12
> **albinootje said:**
> Looking at your screenshot of gparted it shows a key-pair.
What happens when you double-click on it, or try right-click ?
Does it show an error-message ?

at a right-click al options are shown but only information, the last one is available.

at a double-click information is shown. nothin really to change.

---

### Post by carml on 2008-12-12
You can also use a Live version of Gparted,to resize the partitions on your hard disk.
I suggest you to download the Live version of Gparted,burn it to a CD,when reboot from the CD,choosing your language and keyboard settings.
Doing so you'll be able to resize also the second partition,that was in use when you launched Gparted.
Let me know if I could help you :p.

---

### Post by LowSky on 2008-12-12
> **jsf_pp said:**
> 

[IMG]http://i38.tinypic.com/2elqgkn.png[/IMG]


Ok from the image it seems your Extended partiton is actually been formated with other partion insdie of it, see the arrow on the left, click on it it will show you all the other partitons. Delete those if you want to start fresh

---

