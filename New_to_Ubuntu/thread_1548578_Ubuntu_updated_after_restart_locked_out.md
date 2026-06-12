---
title: "Ubuntu updated after restart locked out"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by Truemedia on 2010-08-08
I keep running into problems with grub and I don't understand why when this time around just updating caused it to lock me out with this message popping whenever I try to boot it:

```
"GNU GRUB version 1.98-1ubuntu7
minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>_"
```

I have ubuntu 10.04 installed on an external hard drive (b) with grub on it aswell and nothing else. My windows os is on internal drive (a) and setup so if external drive not on vista loads, and if is on ubuntu loads.

I am really tired of trying to have them coexist, and ubuntu keeps locking up with grub. I have livecd and can print out my fdisk -l if anyone has a solution, or recognizes this error thanks. :(

---

### Post by KCormier on 2010-08-08
Hi Tru.  That's a pretty interesting setup.  Never seen anyone dual boot quite like that (which is probably why you're running into issues).

Chances are, grub updated and didn't configure itself correctly with the new update.  What you'll have to do is reconfigure grub.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Hopefully that can get you started.  If you're still stuck, post back with the output from fdisk -l and also your grub config files.

---

### Post by Truemedia on 2010-08-09
Well iv'e read that link before but it kind of confuses me. I know i can either update grub or reinstall to maybe fix my problem but I don't know the commands.

Can anyone post the update or reinstall terminal commands? (for sdb my ubuntu installation)

---

### Post by Truemedia on 2010-08-09
Ok  I booted up my livecd and got this from fdisk -l in terminal ```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf90c5490

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30402   244196344    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320046346240 bytes
255 heads, 63 sectors/track, 38910 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004571b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38160   306518016   83  Linux
/dev/sdb2           38160       38910     6024193    5  Extended
/dev/sdb5           38160       38910     6024192   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```I don't know where the grub config files are you said to post, if you tell me what directory they are in then I will post them. Cheerz for the help anyways

---

