---
title: "save the worlds biggest noob before i do something worse"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by folabiklan on 2010-03-03
hi please on my desktop i just did a fresh install of mint 8(9.10) and i found that it was running very slowly even more than 9.04 or 9.10 which i have run on the pc with no problem.

so i decided to run fsck but i made the mistake of running it on a mounted partition. it stopped somewhere giving some lines about inode errors. now i cant boot the pc anymore, when ever i start it it doesnt boot grub, it goes into a dark screen and 

grub> filesystem errors

something like that, thats not exactly what it says but you get my drift?
now i tried all cmds i could think of but no way! it does not respond in any way.

iv tried googling but what i see is discouraging, like that my drive has been damaged irreparably?  i have 4 partitions on that drive and windows xp. my very important files are on another partition. what can i do to rescue the other partitions? or just generally?


two, at work i use an acer aspire 5517 and i run karmic in wubi, yesterday i suddenly discovered that the mouse cursor was stuck in the middle and the touchpad does not respond anymore. i have looked in the system settings  and it seems to be ok. and i cant see any keys or combinations of keys on the keyboard to disable the touchpad!
a usb mouse works fine when plugged in. how can i re-enable my touchpad?

---

### Post by folabiklan on 2010-03-03
scratch the touchpad part, its started working again. im pretty sure it was something i did. 

i hate being a noob.

so just my drive and the wrong application of fsck. how can i rescue my drive? and files/partitions

---

### Post by stoogiebuncho on 2010-03-03
Your drive should be fine physically, so don't worry about that.  You will probably need to re-install your operating system. (I've made the same mistake with fsck, and after a reinstall everything was fine.)

If your files were on another partition, they're *probably* fine too.  Try booting up a live CD and see if you can mount the partition that your files are on.  You will probably want to back them up to another location before you reinstall the OS, just to be safe.

---

### Post by Iowan on 2010-03-03
> **folabiklan said:**
> i hate being a noob.Noob is somewhere between "wannabe" and "guru' - so you've progressed more than you may realize...

---

### Post by J V on 2010-03-03
I did this once too, if I remember correctly, booting up again should eventually give you a CLI, just run another fsck and it should have fixed it... I think...

---

### Post by TheXenophobeist on 2010-03-03
I plan to make use of this "noob" term.....

---

