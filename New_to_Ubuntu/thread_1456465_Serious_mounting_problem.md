---
title: "Serious mounting problem"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by Loronal on 2010-04-17
whenever i plud in my usb drive in xubuntu 8.04 it says this:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
i want 9.10 but my internet is really slow and i dont have a cd drive i have a xubuntu 9.10 iso.

---

### Post by theozzlives on 2010-04-17
Have you thought about a USB drive?

---

### Post by Loronal on 2010-04-17
Usb drive what? Im trying to use it and it doesnt work so i really dont know what your talking about

---

### Post by Drenriza on 2010-04-17
What exactly are you trying to do. Are you having booting problems or?

Explain in more detail

If you are having trouble with a corrupt superblock. Then try this command
```
fsck -t [enter ur filesystem here] -b 8193 /dev/sdb1
```
example
```
fsck -t ext2 -b 8193 /dev/hda3
```

---

### Post by Loronal on 2010-04-17
No im in xubuntu and I plud in my flash drive and it says some wierd stuff and i cant browse it. It starting to get really irritating

---

### Post by themusicalduck on 2010-04-17
Install Gparted in synaptic. (Or by typing sudo apt-get install gparted into a terminal).

Once it's installed, go to System > Administration > Gparted. Use the drop down menu on the top right to find and select your USB drive. Then right click on the partition (the big rectangle that would say something like /dev/sdb1 4GiB on it) and select "check". Be careful to select check and not something like delete or format.

After that click apply, and it should do a disk scan of your pen drive. If there are any error messages, then post them here.

---

### Post by Loronal on 2010-04-17
Thanks alot i managed to mount it with gparted and know i will be able to fix this terrible xubuntian disaster:guitar::lolflag::popcorn::confused:

---

### Post by brucewagner on 2010-04-17
I'm sorry, but I had no choice.   I had to comment on the title of this thread.  I thought perhaps it was more appropriate to post it in the [Dr. Ruth Westheimer]("http://en.wikipedia.org/wiki/Ruth_Westheimer") forum.   ;)

---

