---
title: "reformat using ubuntu server CD pls help"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by Fibernet on 2010-01-13
Im using ubuntu server 64 bit. I don't know how to reformat the hard disk using the CD

---

### Post by konqueror7 on 2010-01-13
> **Fibernet said:**
> Im using ubuntu server 64 bit. I don't know how to reformat the hard disk using the CD

hello and welcome to the forums, you may want to take a look at [this]("https://help.ubuntu.com/community/HowtoPartition").:D

---

### Post by JBAlaska on 2010-01-13
System, Administration, open Gparted. right click on the partition and format to your desired filesystem.


Edit: I missed the "Server" part of your post lol.

I beleive the cli version of Gparted is called this way in a term;
```
parted
```

Or you can do this in a terminal;
```
mkfs -t extX /dev/hdxX
``` where xX is the Harddrive and partition you want to format, and extX is the filesystem you want to use, ext3 or ext4 etc.

---

### Post by bolucpap on 2010-01-13
I think that by saying he is using the server version, he has no desktop environment, so he needs a howto that doesn't involve choosing from menus or clicking options, just my opinion

---

### Post by Fibernet on 2010-01-13
thank you so much mmwwaahhh

---

### Post by konqueror7 on 2010-01-13
haha,,,didn't read the server part also, haha,,,i apologize, but there you go...

---

### Post by prshah on 2010-01-13
> **Fibernet said:**
> Im using ubuntu server 64 bit. I don't know how to reformat the hard disk using the CD

I suggest you use cfdisk, rather than parted. It is semi-gui, suitable for console. Parted is rather command-line like; it's better if you are comfortable with it, otherwise not advisable.

Please use sudo with the cfdisk command```
sudo cfdisk
``` You can optionally also specify a device to handle, eg /dev/sda

For formatting your partition, please use mkfs as suggested. You can leave out the "type" option (-t) as mkfs will automatically detect the type and load the appropriate mkfs (eg mkfs.ext3, mkfs.vfat, etc)

---

