---
title: "Grub Loading.. Error 17,Hibernate"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by robertron76 on 2009-05-12
I started my laptop this morning (after it was hibernated yesterday night), and it gave me the error :

Grub Loading.... pls wait
Error 17

I couldn't get the dual boot menu.

Prior to this, yesterday night I did two things :

1. I created a new partition from C Drive, which had Vista partition.Originally there was 123GB Free in 180GB Drive.I created a F partition of 70GB for data,but did not restart the Laptop.Ubuntu 8.04 has its own partition of 40GB,FYI.
2. I hibernated my Vista and went to bed.When I started it this morning, that's when the error came.

I powered off my laptop and restarted and still the same issue.I used LiveCD to boot from first hard disk, but still the same error.

I neither could load Vista, nor Ubuntu to connect to internet.Laptop was stuck with "Error 17".

Hence, I panicked and reinstalled Ubuntu 8.04 on its own partition, from LiveCD and after restart, I was able to logon to Vista and Ubuntu.

Now, what could be the issue? Is it the hibernate or creating the partition for data?

I wanna try the hibernate on Vista and see if this happens again, what should I do? I don't have an alternate PC to connect and check ubuntu forums.

---

### Post by Gone fishing on 2009-05-12
This is a problem if you change the partitions so that grub can mount the partitions:

> Error 17 indicates GRUB can't id the partition type. Check [http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting) for more info. Here is the relevant entry:
"17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB."

I'd boot from a live CD and fix grub:

Boot the live CD, and from the Terminal type

sudo grub

At the grub promp type

find /boot/grub/stage1

It will tell you where the root partition is something like (hd1,0)
type that in after root

root (hd1,0)

setup (hd0)

quit

Then it should be fixed

---

