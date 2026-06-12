---
title: "&quot;read error&quot; drive wont boot"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by kochinc on 2011-03-29
When I try to restart my computer after installing Ubuntu on a new 500 gig hard drive I get a "read error".  I went back to the live CD and looked for the grub.  It said it wasn't installed so I installed it but now I get an error 15 when looking for it.  I have installed 4 times now and still not booting.  The Hard drive is a white label SADA with and IDE converter.  CMOS sees it fine and it shows healthy in Disk Utility.  Can I resize the boot partition if it is too large or what does one suggest.  Thanks

---

### Post by collisionystm on 2011-03-29
are you getting the grub error 15 every time or just read error

---

### Post by jtarin on 2011-03-30
This should give you a better understanding of the problem and what to do.
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by kochinc on 2011-03-30
I get a read error when trying to boot the Hard drive and Error 15 in grub when looking for the
"boot/grub/stage1".  I tried to send a screen shot but it is too small to see.  Will try again.

---

### Post by kochinc on 2011-03-30
I ran the suggested command and this is what it returned.


ubuntu@ubuntu:~$ sudo bash ~/desktop/boot_info_script*.sh
bash: /home/ubuntu/desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$

---

### Post by Hedgehog1 on 2011-03-30
kochinc,

The issue you are having (and the link that jtarin gave you) are the same thing:

You have legacy grub (**GR**and **U**nified **B**oot loader) on this drive as well as the current grub2.

It looks like you copied your data from an earlier Ubuntu install to the new drive, or installed the old version then then the new version of Ubuntu on the drive.

You have a couple of choices:

(1) Purge the old grub and install the new grub (you can do this from the LiveCD/LiveUSB)  This will preserve and data you have on the drive.

(2) If you have no data on the drive yet, a clean install of Ubuntu (delete the current partitions and make new ones using gparted from the LiveCD/LiveUSB) would also solve this.

Do you need guidance in either of these processes?

***The Hedge***

:KS

---

### Post by kochinc on 2011-03-30
I think I my lack of understanding is due to partitioning.  Do I partition the HD now and then reload Ubuntu to the disk or what?  I would like to make about 3 partitions, a 20 gig of Linux boot and a couple of 200+ for the rest.  Is that possible and what are the commands to make that a reality?  I apologize, I worked in DOS for too many years.

---

### Post by kochinc on 2011-03-30
I am enclosing a screen-shot of my latest partition configuration.  If you see something out of ordinary let me know.  It has NO data in the drive yet.

---

