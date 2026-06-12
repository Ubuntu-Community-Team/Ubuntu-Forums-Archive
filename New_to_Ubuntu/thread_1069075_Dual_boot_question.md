---
title: "Dual boot question"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by keith1 on 2009-02-13
I'm using SuperUbuntu as my main OS. I want to dual boot with Kubuntu. I'll try to put this information in some logical order.

First of all, I've dual-booted several distros before with no problems on this machine - but it's not working this time. I shrunk down SuperUbuntu to about half of my HDD space (using Gparted) and installed Kubuntu on the remaining unallocated space. Fine so far... but when I boot the computer I don't have the option to select which OS to use, as I've always had in the past - It just boots SuperUbuntu.

I've been trying alot of odds-and-ends stuff from Googling, but I'm totally lost at this point, and decided to stop and ask. Kubuntu doesn't seem to be mounted to start off with, and I'm not sure how to do that -

keith@keith-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             18737268   4877940  13097852  28% /
tmpfs                   224632         0    224632   0% /lib/init/rw
varrun                  224632       208    224424   1% /var/run
varlock                 224632         0    224632   0% /var/lock
udev                    224632      2768    221864   2% /dev
tmpfs                   224632       348    224284   1% /dev/shm
lrm                     224632      2004    222628   1% /lib/modules/2.6.27-11-generic/volatile
keith@keith-desktop:~$

BTW - SuperUbuntu is on sda1 ext3, and Kubuntu is on sda8 ext3.

I'm so......... lost right now, where do I start?  Please let me know what additional information you need.

Thanks,   Keith

---

### Post by bodhi.zazen on 2009-02-13
When you install kubuntu you need to install grub to you MBR. Typically this happens automatically.

My guess is either the install failed (is there anything on /dev/sda8 ??? ) or you did not install grub properly.

You can manually configure grub , several suggestions in these links :

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817") 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by keith1 on 2009-02-13
When I installed Kubuntu I just let it do it's own thing, as I've done in the past with no problems. As far as a "bad install" I actually deleted sda8, burned a new live Kubuntu cd and reinstalled. Like I said, everytime I've dual booted distros before I've always had the option to select which OS to use.

Gparted does show both partions - but I can't figure out how to copy it here. It doesn't show a mount point.


Edit - forgot to mention, the info in the links is way over my head - any other info I can supply to help out here?

---

### Post by bodhi.zazen on 2009-02-13
From teh second link :

boot a live cd

Open a terminal.

```
sudo gurb
```

At the grup prompt

looks like 

grub >

type these commands :

```
root (hd0,7)
setup (hd0)
```

quit grub and reboot.

---

### Post by keith1 on 2009-02-13
Didn't work - here's what I got

grub> root (hd0,7)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

Hope this info helps

---

### Post by bodhi.zazen on 2009-02-13
Well something has gone wrong with grub and your Kubuntu installation. could be a bad burn, did you check the CD for defects ?

Could be you did not install grub , by your description accidentally.

Since this is a fresh install I suggest you boot the Cd and check it ofr errors (it is an otion on the initial boot screen). If there are none, reinstall and make sure you install gurn to your MBR.

Otherwise you will need to set up grub ;)

You seem reluctant to read links, or do not understand them so there is always SuperGrub :

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

download supergrub, burn it to cd, and boot it up.

---

