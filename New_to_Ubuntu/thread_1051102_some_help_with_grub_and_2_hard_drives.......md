---
title: "some help with grub and 2 hard drives......"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by techno-mole on 2009-01-26
hello.

i have just installed a new hard drive in my kids pc, this is so they can dual boot with xp (which is going to be their games hard drive, they do everything else with ubuntu)

but i have a small problem, when i went to install xp on the second hard drive it woudlnt install as it didnt recognise the partitions on the ubuntu hard drive, so me in my wisdom (or lack of it) pull the sata lead out of the ubuntu hard drive and went ahead and installed xp to the new drive, can you see where this is going ?

basically i want to get it set up so that when the system boots, the kids will get what i get (i dual boot with xp) that being a menu that has linux as the first option, and then windows at the bottom of the list, so that when they want to play games the scroll down the list and select xp.

normally what i do is to install xp first, then install ubuntu as the install process takes care of this for you, i have tried editing grub before, with not so good results.

so im after an easy how to on how i can get grub installed so that my kids can select which operating system they want to boot from.

cheers in advance for any help.

---

### Post by Elfy on 2009-01-26
Try adding this to menu.lst first

```
gksudo gedit /boot/grub/menu.lst
```

```
title XP
root  (hd1,0)
savedefault
makeactive
map   (hd0) (hd1)
map   (hd1) (hd0)
chainloader    +1
```

If that doesn't help post

```
sudo fdisk -l
```

---

### Post by techno-mole on 2009-01-27
hello again, sorry it took so long to get back to you, getting the kids off the pc long enough fr me to do anything with it isnt always easy.

okay, so that worked, i now can select what to boot from the grub list, but how do i get the system to automatically show the list ?

on my system, when it boots the grub list comes up automatically, and then it says the default will be loaded, booted and theres a timer, but on my kids system i have to hit escape within 3 seconds in order to get to the grub menu, is there a way to either give it more time, or get it to load the menu automatically ?

cheers.

---

### Post by Elfy on 2009-01-27
Yep easy done :)

Backup the file and open for editing

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.2701
gksu gedit /boot/grub/menu.lst
```

Close to top of file there are 2 lines which intersest you here

timeout
#hiddenmenu

change the timeout to suit you and make sure there's a # before hiddenmenu, save and close.

---

### Post by techno-mole on 2009-01-27
cheers, worked like a charm, now all i have to do is get xp updated.
many thanks

---

### Post by Elfy on 2009-01-27
that'll be fun then ....

---

