---
title: "Ubuntu not loading properly"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by Master Chimp on 2011-05-24
So I installed Ubuntu 10.10 yesterday to dual boot with Windows 7 and it worked beautifully even until this morning. Today I tried to load it up and it first hung at Checking battery...when I reset, it said to login through the terminal rather than bring up my GUI. I logged in and then tried several fixes I saw here including sudo apt-get install ubuntu-desktop and that didn't work and neither did just startx. What can I do? Thanks in advance for helping out this noob.

---

### Post by garvinrick4 on 2011-05-24
Boot into recovery with internet conection or Terminal: And copy and paste these one at a time. 
sudo apt-get install aptitude
aptitude show gdm
aptitude show xorg
apitude show ubuntu-desktop
Make sure they all (the 3 with show in them) say installed
#If all installed go below, if not installed, install it and reboot. sudo apt-get install "package name" (without quotes)
```
 
#Put in Live CD (install cd using Try ubuntu with internet working (run firefox and see if you can get on line first): and copy and paste:
#first use this to find your linux install (it will say Linux if you want to post we can tell you what yours is.)
sudo fdisk -l (lower case L)
#I will use sda5 for this change to what yours is. Copy and paste these one at a time.
sudo e2fsck /dev/sda5

sudo mount /dev/sda5 /mnt
                                   
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done 

sudo cp /etc/resolv.conf  /mnt/etc/resolv.conf
                                  
sudo chroot /mnt

dpkg --configure -a

apt-get -f install

apt-get update && apt-get upgrade

dpkg --configure -a

exit
                                  
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt$i ; done

sudo umount /mnt

sudo reboot

Hopefully it will have fixed. Just running a disk check, looking for broken packages to fix. 
Upgrading and looking for broken packages again. Unmounting
*** I know you are new and this looks strange but it just checking your filesystem and trying to fix things
that we do not know what is wrong. Just follow instructions and copy and paste and hit enter in a terminal. 
ctrl/alt/t if you do not know how to open a terminal.

```

---

