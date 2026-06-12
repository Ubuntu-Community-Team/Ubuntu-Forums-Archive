---
title: "What is this error means ?"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by levis lover on 2010-07-11
```

sudo apt-get install grub

```

**Output**
```

Err http://in.archive.ubuntu.com karmic/main grub 0.97-29ubuntu59
  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/g/grub/grub_0.97-29ubuntu59_i386.deb  Could not resolve 'in.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

What should i do ?

---

### Post by mick222 on 2010-07-11
Grub-pc should be installed on your system. Why are you trying to install grub.

---

### Post by levis lover on 2010-07-11
I had messed up everything..
now i don't know what to do ?
System is not showing the bootloader..

---

### Post by philinux on 2010-07-11
Run this from the livecd and post back the result.txt.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by levis lover on 2010-07-11
Here are the results..

---

### Post by drs305 on 2010-07-11
It looks like you had Grub 2 installed (the Grub 2 files are in sda6) but now you've (partially) installed grub legacy.

To reinstall Grub 2, run a recent copy of the LiveCD, mount sda6 and install grub-pc to the MBR and its files to sda6:

```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```
Note that it is **sda** and NOT **sda6**

Reboot and Grub2 should work.

---

### Post by levis lover on 2010-07-11
Wow,
you guys don't know how greatful i am for all your support and help..
It got fixed in a second..
I have been trying to fix it for the past 7 hours..
I tried each and every command i could find after Google-ing..
You guys Rock !!

---

