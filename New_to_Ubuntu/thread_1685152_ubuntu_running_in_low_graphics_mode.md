---
title: "ubuntu running in low graphics mode"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by buffaloeb23 on 2011-02-10
I'm new to Linux and installed Ubuntu 9.04 over the summer in a dual boot configuration with Windows XP on a desktop that I built myself. I have been running Ubuntu 10.10 32 bit for a number of weeks without any problems . Today on startup I get a message about running in low graphics mode. After I click OK I get a menu which gives me the choice of running in low graphics mode, reconfigure graphics, troubleshot the error or exit to console login. If I try to use the first 3 options they just loop back to the first screen. If I choose exit to console loigin it get as far as ....Checking battery state... and hangs.
I have tried using the recovery mode from the grub menu as well. I am able to access the menu. I tried the option to resume normal boot, repair broken packages, and run in failsafe  graphic mode. None of these work. When I choose them I see text strings running and then a command prompt appears allowing a login. I log in but nothing happens
I have tried booting into my Win XP partition and everything seems to work fine. I I have an ATI Radeon HD 4200 video card and have never had a problem with it. I t was running 10.10 fine until today. I am guessing that the problem really isn’t a graphics card issue but I am not sure. I really would prefer not to have to reinstall if I can avoid it. Any help would be greatly appreciated.

---

### Post by searchfgold6789 on 2011-02-10
Welcome to the forums.
Since you apparently can't run commands right now, you'd have to first boot from a Live CD. Open a terminal there and type:
```
sudo mount /dev/sdXX /mnt
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
sudo chroot /mnt
```Replacing /dev/sdXX with the partition you are having problems with.
Then type ```
sudo dpkg-reconfigure -phigh xserver-xorg
```...If that doesn't work I would recommend purging and reinstalling gdm.

---

### Post by buffaloeb23 on 2011-02-10
thanks for your help. I have some questions. Where do I find the name of the partition? what of the dev/sdxx string do I replace? is it the XX? 
For my own knowledge can you explain the purpose of the commands I am entering into the terminal Thanks again

---

### Post by searchfgold6789 on 2011-02-10
To find out what to replace /dev/sdXX with, look in GParted from Applications>System
Find the hard disk partition you installed ubuntu on, GParted will label it as something like /dev/sda1 or something.

---

### Post by buffaloeb23 on 2011-02-10
I tried to follow your instructions; I am attaching a screen shot from GParted
I put the code into the terminal and this is what i got

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
mount: /dev/sda5 already mounted or /mnt busy
mount: according to mtab, /dev/sda5 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev  /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /dev/pts  /mnt/dev/pts
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys  /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# sudo dpkg-reconfigure -phigh xserver-xorg
sudo: unable to resolve host ubuntu
root@ubuntu:/# 

I am not sure I understand what happened

---

