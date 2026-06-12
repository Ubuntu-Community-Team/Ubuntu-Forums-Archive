---
title: "Accessing local hard drive using live CD"
date: 2005-09-02
forum: Networking &amp; Wireless
---

### Post by Old *ix Geek on 2005-09-02
I'm using a 5.04 live CD on one of my 'doze XP desktops, and I'm stumped as to how to access its local hard drive.  I had previously used a Linspire live CD on this same box, and it was very straightforward: system > disks > dos2 gave me full access to all files on the hard drive.

The first time I booted this box up (yesterday) with the 5.04 live CD, it found both of the 'doze computers on the network--which included this box.  In other words: places > network servers > windows network > workgroup > PC1  PC2.  Today, however, PC2 (this box) is missing.  Regardless, even when it was there, attempting to access it just yielded an error message about not being able to display its contents.

I've also tried mounting it: connect to server > windows share > (and then filling in its info), with the same result.  It's there, but I cannot access its files.

I have full access to the other 'doze PC on this network; it's just the LOCAL drive that I can't find!  Any/all advice will be greatly appreciated!

(PS  As per my user name, I AM an old *ix geek.  However, using *ix on 'doze boxes is new to me.)

---

### Post by cwaldbieser on 2005-09-02
[QUOTE=Old *ix Geek]I'm using a 5.04 live CD on one of my 'doze XP desktops, and I'm stumped as to how to access its local hard drive.  I had previously used a Linspire live CD on this same box, and it was very straightforward: system > disks > dos2 gave me full access to all files on the hard drive.

The first time I booted this box up (yesterday) with the 5.04 live CD, it found both of the 'doze computers on the network--which included this box.  In other words: places > network servers > windows network > workgroup > PC1  PC2.  Today, however, PC2 (this box) is missing.  Regardless, even when it was there, attempting to access it just yielded an error message about not being able to display its contents.

I've also tried mounting it: connect to server > windows share > (and then filling in its info), with the same result.  It's there, but I cannot access its files.

I have full access to the other 'doze PC on this network; it's just the LOCAL drive that I can't find!  Any/all advice will be greatly appreciated!

(PS  As per my user name, I AM an old *ix geek.  However, using *ix on 'doze boxes is new to me.)[/QUOTE]
You should be able to simply mount the hard drive.  If it is an IDE drive, it is probably something like /dev/hda1.  If it is a SATA drive, maybe something like /dev/sda1.  The filesystem will either be some sort of FAT or NTFS depending on your Windows filesystem.  If NTFS, you must mount it read-only.

---

### Post by Old *ix Geek on 2005-09-03
Well, I'm still stumped.  :-(

Yes, it's an IDE drive, and here's what I've tried most recently:

$ mkdir tempdir
$ sudo mount -t ntfs /dev/hda2 tempdir

which yields:

mount: unknown filesystem type 'ntfs'

---

### Post by s_p_a_r_k_y on 2005-09-04
[QUOTE=Old *ix Geek]Well, I'm still stumped.  :-(

Yes, it's an IDE drive, and here's what I've tried most recently:

$ mkdir tempdir
$ sudo mount -t ntfs /dev/hda2 tempdir

which yields:

mount: unknown filesystem type 'ntfs'[/QUOTE]


i don't believe that ubuntu ships with ntfs support, however it can be installed easily through apt-get or Synaptic. However since your running the liveCD version you may not be able to. Try knoppix which includes ntfs read support and experimental write support

---

