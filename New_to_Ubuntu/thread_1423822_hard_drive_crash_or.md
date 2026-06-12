---
title: "hard drive crash or ?"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by AutumnPhoenix on 2010-03-07
Hello

been running xubuntu for 3 years now.

yesterday my computer just didn't want to start up.

grabbed my cd and am running xubuntu live right now.

it won't mount my volume.
I get this message:
> mount: wrong fs type, bad option, bad superlock on /
dev/sda1, missing codepage or helper program, or other error

In some cases useful is found in syslog - try
dmesg I tail or so


and when I run dmesg it stops at this

> [  163.572000] ath0: no IPv6 routers present
[  637.388000] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240).
[  662.664000] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240).


---

### Post by Robster2 on 2010-03-07
I don't know what the problem is but I am sure you will need the system rescue CD

[http://www.sysresccd.org/](http://www.sysresccd.org/)

You might as well download it and burn it while you are waiting for more replies.

---

### Post by AutumnPhoenix on 2010-03-07
I can't make a CD, though, because this is my only computer and the CD rom drive is currently occupied by the live CD.

*edit* I see you can run it off of USB stick.  When the local stores open I'll go get one.

---

### Post by halitech on 2010-03-07
can you browse to the hard drive and post the results of
```
gedit /etc/fstab
```

---

### Post by AutumnPhoenix on 2010-03-07
It's asking me to install gedit

should I do that?

---

### Post by halitech on 2010-03-07
sorry, forgot you were on Xubuntu. change it to 
```
mousepad /etc/fstab
```

---

### Post by AutumnPhoenix on 2010-03-07
Here it is:

> unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

---

### Post by halitech on 2010-03-07
ummmm okay. that is a weird looking fstab. how did you install Xubuntu? is it the only OS on the drive?

wait, did you run the command I gave you? I'm thinking that actually may be for the live cd. you might need to actually browse the hard drive and find the file on the hard drive and open it with mousepad and read it.

---

### Post by AutumnPhoenix on 2010-03-07
how would I read the HD?  What would the command be if it's not mounted?

---

### Post by halitech on 2010-03-07
what is the output of
```
sudo fdisk -l
```

---

### Post by AutumnPhoenix on 2010-03-07
This is the readout that I get.  It is a 40 gig drive.  I know that's small but it was decent 4 years ago when I got the toppy.

> Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

---

### Post by halitech on 2010-03-07
ok, lets try this

```
mkdir harddrive
```
```
sudo mount /dev/sda1 ~/harddrive
```
then see if you can see the files on the hard drive. they should be in /home/<username>

---

### Post by AutumnPhoenix on 2010-03-07
> **halitech said:**
> ok, lets try this

```
mkdir harddrive
```
```
sudo mount /dev/sda1 ~/harddrive
```
then see if you can see the files on the hard drive. they should be in /home/<username>

I get the same darned mount error
> 
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


---

### Post by halitech on 2010-03-07
you could try an fsck on it
```
sudo fsck /dev/sda1
```

---

### Post by AutumnPhoenix on 2010-03-07
output of command

> fsck.ext3: Filesystem has unsupported feature(s) while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by egalvan on 2010-03-07
> **AutumnPhoenix said:**
> I can't make a CD, though, because this is my only computer and the **CD rom drive is currently occupied by the live CD.**

*edit* I see you can run it off of USB stick.  When the local stores open I'll go get one.


PartedMagic LiveCD, which has some good "rescue" type software, and it's a small 44M download...
it runs in RAM and releases the optical drive for other uses...
it's the one I use the most, for rescue work...
( I am a subscriber, it's worth supporting good software )

partedmagic.com


Or download Puppy Linux, which also runs in RAM and frees the optical drive for other uses...

---

