---
title: "HP driver"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by recycledhippy on 2009-01-19
I've been trying to load a driver for my new hp printer and it hasn't been working. It is a hp Deskjet f2240. I went to the HP website for a linux driver. I followed the link they had and downloaded it. Started to install it and it was going ok till it gets to a point. It tells me to make sure I have the reporitories for univerese and multiverse open and the ubuntu main one. it also says to make sure the cd rom is not selected. so it starts to go and it never works it times out and asks if I have the cd enabled and that I shouldn't.

/home/jason/Desktop/Screenshot-Software Sources.png
 once again what am I doing wrong?

---

### Post by mlentink on 2009-01-19
> **recycledhippy said:**
> 
/home/jason/Desktop/Screenshot-Software Sources.png
 once again what am I doing wrong?

Maybe you could repost that screenshot?

DO you really have universe and multiverse selected and the cd-rom deselected in your sources? If not we can guide you through it, it's easy.

---

### Post by compiledkernel on 2009-01-19
[http://openprinting.org/show_printer.cgi?recnum=HP-Deskjet_F2224_All-in-one](http://openprinting.org/show_printer.cgi?recnum=HP-Deskjet_F2224_All-in-one)
[http://openprinting.org/show_printer.cgi?recnum=HP-Deskjet_F2280_All-in-one](http://openprinting.org/show_printer.cgi?recnum=HP-Deskjet_F2280_All-in-one)

the 2224 and the 2280 are both heavily supported via the hpijs driver. 

I would imagine that the same holds true here. You should be able to select that driver from the Printer Add menu, or if you consider yourself a little more tech savy, just browser to 

[http://localhost:631](http://localhost:631)

---

### Post by recycledhippy on 2009-01-19
<a href="http://s553.photobucket.com/albums/jj370/jbrockk13/?ac




try this. Icant seem to get it to post in here

---

### Post by perce on 2009-01-19
Most HP printers are plug-and-play. Have you tried plugging it in before starting the drivers hunt?

---

### Post by recycledhippy on 2009-01-19
[IMG]http://ubuntuforums.org/picture.php?albumid=855&pictureid=2915[/IMG]

---

### Post by Captain_tux on 2009-01-19
**HPLIP** (HP Linux Imaging and Printing) worked perfectly for me... printing, scanning, everything:

[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

Here's the thread it came from:

[http://ubuntuforums.org/showthread.p...highlight=5180](http://ubuntuforums.org/showthread.p...highlight=5180)

Pay attention as the auto compiler runs (it may call up certain commands), but it's easy and works like a charm.

---

### Post by perce on 2009-01-19
> **Captain_tux said:**
> **HPLIP** (HP Linux Imaging and Printing) worked perfectly for me... printing, scanning, everything:

[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

Here's the thread it came from:

[http://ubuntuforums.org/showthread.p...highlight=5180](http://ubuntuforums.org/showthread.p...highlight=5180)

Pay attention as the auto compiler runs (it may call up certain commands), but it's easy and works like a charm.

hplip is installed by default, why do you need to compile it from source?

---

### Post by Captain_tux on 2009-01-19
> **perce said:**
> hplip is installed by default, why do you need to compile it from source?

HPLIP is installed on Hardy by default? Didn't know that...

Regardless, my HP 5180 was a brick until I ran that auto compiler... and like I said, it works beautifully now.

EDIT: HPLIP **is** installed by default on Hardy... just verified it. Not sure why my printer didn't work until I went the way of the auto compiler.

---

### Post by perce on 2009-01-19
> **Captain_tux said:**
> HPLIP is installed on Hardy by default? Didn't know that...

Regardless, my HP 5180 was a brick until I ran that auto compiler... and like I said, it works beautifully now.

Yes it is. Maybe you needed a more recent version because your printer is newer than mine? who knows...

---

