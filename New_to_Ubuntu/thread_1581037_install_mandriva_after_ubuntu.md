---
title: "install mandriva after ubuntu"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by abs_kkk on 2010-09-24
i want to install mandriva distro (kde 2010 version) on a separate partion in my HDD , will it cause an problems with my grub? , i already have ubuntu 9.10 installed on the same HDD

---

### Post by Rubi1200 on 2010-09-24
If there is an option during the installation of Mandriva to not install a bootloader, I would go with that. Then, after installation go into Ubuntu and run ```
sudo update-grub
``` which should then pick it up and add it to the menu.

Otherwise it will overwrite GRUB and use its bootloader, which is, I believe, Lilo and you would have to reinstall GRUB (which is not a problem)

---

### Post by beickus on 2011-06-10
> **Rubi1200 said:**
> If there is an option during the installation of Mandriva to not install a bootloader, I would go with that. Then, after installation go into Ubuntu and run ```
sudo update-grub
``` which should then pick it up and add it to the menu.

Otherwise it will overwrite GRUB and use its bootloader, which is, I believe, Lilo and you would have to reinstall GRUB (which is not a problem)


well after doing that- ( update grub from ubuntu) when i try to boot to mandriva i have kernel panic 

the grub is on sda (ntfs partition) ubuntu is on sda2 mandriva on sda6, sda7 swap, sda8 - 

during mandriva installation i put grub/ lilo on sda6 as there was no option to pass this...\

---

### Post by beickus on 2011-06-29
update :
i tried to install again mandriva - so i have this situation on my second hdd

sdb: sdb5-ntfs, sdb2-xubuntu, sdb6-mandriva root, sdb7-swap, sdb8- home mandriva
but the mandriva bootloader was setup on... sda- ntfs windows !
if i want to boot windows i have to choose device list, then boot second drive sdb: there at xubuntu grub fortunately there is a windows entry for the other disk, sda- windows ! 
if i let the computer boot on its own it boots sda --mandriva which is as said on sdb6!
i know i can repair windows MBR with easyBSD, but is there a way i can sort this mess and get the two linux entries mandriva-xubuntu when i boot from sdb?
without risking ofc

---

### Post by oboedad55 on 2011-06-29
For some reason grub2 mis-labels the Mandriva boot partition. Have a look here; [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2). It should explain how to create a custom grub entry, which is what I did to get Mandriva to boot. BTW, when I installed Mandriva I just had it point its bootloader to the Mandriva /root partition.

---

