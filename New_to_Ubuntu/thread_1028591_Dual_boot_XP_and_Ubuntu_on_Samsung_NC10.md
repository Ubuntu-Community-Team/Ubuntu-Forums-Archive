---
title: "Dual boot XP and Ubuntu on Samsung NC10"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by psphunt on 2009-01-02
hi im new here and dont know where to post this so mods please move it to the right section if i am in the wrong.

I am going to buy a Samsung NC10 and wnat to install ubuntu and xp, with xp starting as defalt after 15 sec or so.

how would i go about doing this?

thanks
:D

---

### Post by armandh on 2009-01-03
this is what worked for me with a dell mini9

use parted magic [a live partition utility] to set up a primary ntfs partition for xp leaving about 7G unpartitioned

install xp

install ubuntu and select largest unpartitioned space at the partition menu.

in ubuntu install a grub editor

edit the grub to make xp the default [I didn't]

FYI....GRand Unified Bootloader [grub]

.

---

### Post by psphunt on 2009-01-03
is this a goog tut for changing GRUB
```
http://xibex.blogspot.com/2008/05/change-boot-option-order-grub-ubuntu.html
```or this one
```
http://ubuntu-tutorials.com/2006/12/29/tweaking-grub-ubuntu-510-6061-610/
```

---

### Post by Sef on 2009-01-03
1) Moved to Absolute Beginners.

2) Read [Psychocats]("http://psychocats.net/ubuntu").  There is a pictoral tutorial on how to dual boot with the live cd.

---

### Post by psphunt on 2009-01-03
cant find it

---

### Post by XopherH on 2009-01-09
[http://ubuntuforums.org/showpost.php?p=6395188&postcount=12](http://ubuntuforums.org/showpost.php?p=6395188&postcount=12)

---

### Post by octotracy on 2009-01-11
there's a GUI (right terminology?) to allow you to change grub settings without going into the menu.lst. 

Search for "startup manager" in the synapticpackage maager and install it. 
I found it much easier than trying to figure out exactly which bit to change.

---

### Post by octotracy on 2009-01-11
there's a GUI (right terminology?) to allow you to change grub settings without going into the menu.lst. 

Search for "startup manager" in the synapticpackage maager and install it. 
I found it much easier than trying to figure out exactly which bit to change.

---

### Post by octotracy on 2009-01-11
there's a GUI (right terminology?) to allow you to change grub settings without going into the menu.lst. 

Search for "startup manager" in the synapticpackage maager and install it. 
I found it much easier than trying to figure out exactly which bit to change.

---

### Post by Yellowpolkadot1040 on 2009-03-19
try this

[https://help.ubuntu.com/community/NC10](https://help.ubuntu.com/community/NC10)

---

