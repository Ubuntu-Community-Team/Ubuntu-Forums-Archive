---
title: "Grub fix without working Ubuntu"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by jfweiss on 2011-01-18
I'm having a problem that is related to Ubuntu, but not necessarily about Ubuntu.

My sister wanted to try out Linux so I dual booted her laptop (which was on Vista) with Ubuntu 10.10. It worked fine for a few months but about a week ago it had a major error. Grub would load fine, but if you selected Ubuntu it would give you a string of errors. My question isn't about fixing this problem it's about a problem I caused while trying to fix this one.

I had been attempted to run a disk checker on the partition with Ubuntu on it, but anytime I tried reading the drive, it would crash. I was using a liveUSB of Ubuntu and when I couldn't get that to work, I tried a live puppy distro. Now here's where I think I screwed up. Somehow, while I was trying things with puppy, I damaged the grub files. I've fixed grub on my computer fairly quickly before. 

Here's the problem: every fix for grub I know of requires mounting a working copy of Ubuntu, which I can't.

I can't use any fixes from microsoft because the cd drive is broken and as far as I can find there are no MS USB boot options.

PS. Because the CD drive is broken I use a live USB stick to boot linux.
PPS. I've also tried to use the PLOP boot program, but I was unable to get it to work

---

### Post by Quackers on 2011-01-18
You can purge and re-install grub from the live cd/usb desktop. This will create new grub files. You need an internet connection.
In the guide below scroll down to the "why chroot?" section and use that.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by garvinrick4 on 2011-01-18
If you have a live USB of Ubuntu in the same architecture 32 or 64 bit we can load grub
into mbr with chroot command. Just need the sda# that your install is on. I will use sda1 use your own: Can get your own by:
```
sudo fdisk -l
``` (lower case L)
                          ```
sudo mount /dev/sda1 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
 

 
``````
grub-install --root-directory=/mnt /dev/sda
``````
update-grub
``````
exit
```                          ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
 
```Now reboot into HDD and go to Ubuntu and:
```
sudo update-grub
```
## This is just to put grub in mbr not to fix an unclean system: If you need that it is another set of code:

---

### Post by jfweiss on 2011-01-18
I don't have access to the system again until tomorrow, so I will try your suggestions then. 

If I am understanding the steps in them right, I don't think they will work. Both solutions require the Ubuntu partition to be mounted, but that wont work. That was my first response to grub failing but whenever I try to mount the drive I get an error. I wasn't even able to run a diagnostic tool on it without the tool crashing. 

What I need is some way to install grub using only a USB stick, without a Linux OS on the hardrive. I don't even care if it's grub that I get working, any boot loader that can see windows (and preferably Ubuntu) would work.

---

### Post by garvinrick4 on 2011-01-18
#This will boot windows only.
#In live usb you have with internet connected:
```
sudo apt-get lilo
```
```
sudo lilo -M /dev/sda mbr
```
Will say error ignore we only need mbr
#Reboot into Hard Drive

---

### Post by jfweiss on 2011-01-19
That worked great, thank you so much

---

