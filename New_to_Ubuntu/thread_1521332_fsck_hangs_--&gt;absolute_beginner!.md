---
title: "fsck hangs --&gt;absolute beginner!"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by kovacslajcsi on 2010-06-30
Hi,

I'm running ubuntu 9.04. The machine is running 7/24, all the time. Yesterday I had a power failure, at the next boot fsck hangs after some minutes, with exit code 1. After it boots normally, and seems to be working.. I tried to reboot, it was the same..

I'm absolute beginner, so NO knowledge about fsck, or linux file systems...

How can i repair this, without data loss? (the machine is a security video server..) 

I can boot from a live CD, from an USB CD (the machine is small, mini ITX board, without integrated drives..)

What is the next step? 

after the Live CD boot, how I unmount the drive? How to run fsck, etc..

Thank you for any kind of help.

---

### Post by jlenain on 2010-06-30
Hi kovacslajcsi,

After having booted from a live CD, you could maybe first try to run the partition editor (Under GNOME: System -> Administration -> GParted), and do a "Check" on your root partition.

Cheers

---

