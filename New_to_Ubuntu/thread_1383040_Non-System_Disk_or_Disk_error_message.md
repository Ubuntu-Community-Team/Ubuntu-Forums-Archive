---
title: "Non-System Disk or Disk error message"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by Pedantic Dandelion on 2010-01-16
Okay.

I am trying to boot my new ubuntu 9.10 system on a HD Compaq Intel 83.

When I turn it on, it gives me said message, and will not boot ubuntu from my hard drive.

I have tried reinstalling it and it still won't read it. I have read a few threads about grub and boot up files, but I can't seem to get to any command prompt that will aloow me to do this. (nor do most of these threads mention how)

I'm at a loss, and my cd rom is much to slow to continue booting up from there. Any thoughts?

---

### Post by cbabbage on 2010-01-16
Is your BIOS on the correct setting, to boot from the hard drive? Sounds like it might possibly still trying to boot from the DVD rather than the hard drive.

---

### Post by Pedantic Dandelion on 2010-01-16
> **cbabbage said:**
> Is your BIOS on the correct setting, to boot from the hard drive? Sounds like it might possibly still trying to boot from the DVD rather than the hard drive.
I checked the bios. It boots from the hard drive and all the settings are normal.  I even tried to boot it without the CD ROM and it just gives me the non system disk message

---

### Post by warfacegod on 2010-01-16
This sounds like GRUB2 (not GRUB) needs to be reinstalled. There are step by step instructions here:

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by Pedantic Dandelion on 2010-01-17
> **warfacegod said:**
> This sounds like GRUB2 (not GRUB) needs to be reinstalled. There are step by step instructions here:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

It seems that grub 2 is already installed. 
The codes didn't work 
```
sudo grub-install --root-directory=/mnt/ /dev/sdX
``` included,
with the parameters use.

But I ended up using the disk utility application that comes with Ubuntu 9.10.
It also seemed to recgonize the MBR at start up, but now says theres an error
loading the system.

Now I am unsure what type I could put as the file system type. It gives me a
number of options including Linux (0x83) as default, and various verisons
of fat, solaris, ect.

---

### Post by warfacegod on 2010-01-17
> **pedantic dandelion said:**
> it seems that grub 2 is already installed. 
The codes didn't work 
```
sudo grub-install --root-directory=/mnt/ /dev/sdx
``` included,
with the parameters use.

But i ended up using the disk utility application that comes with ubuntu 9.10.
It also seemed to recgonize the mbr at start up, but now says theres an error
loading the system.

Now i am unsure what type i could put as the file system type. It gives me a
number of options including linux (0x83) as default, and various verisons
of fat, solaris, ect.

0x83

---

### Post by Pedantic Dandelion on 2010-02-19
Now!

I got Grub 2 installed. However, now it doesnt have the grub menu, and it's not set to default when I try to boot it.

I went through this code-
```
1. ls 
    2. set prefix=(hdX,Y)/boot/grub  
    3*. set root=(hdX,Y) 
    4. set 
    5. ls /boot 
    6. insmod /boot/grub/linux.mod 
    7*. linux /vmlinuz root=/dev/sdXY ro 
    8. initrd /initrd.img 
    9. boot 

```







but  it cannot find any intrid files. Not really sure what to do next.

---

