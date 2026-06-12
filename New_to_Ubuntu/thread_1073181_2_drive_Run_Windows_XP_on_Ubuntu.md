---
title: "2 drive Run Windows XP on Ubuntu"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by Demonlord666000 on 2009-02-18
I have searched the forums but have not come across anyone trying to do this or anyone who has asked for help on this but here goes.

I have Windows XP MCE installed on HD 0 and Ubuntu on HD 1 
HD 0 - 160GB SATA II (MBR is Windows native)
  Partition 1 - 74GB Windows Installation
  Partition 2 - 74GB Spare for my media (moves, music, ect.)
HD 1 - 40GB IDE (MBR is Grub)
  Partition 1 - 35GB Ubuntu 8.10 Installation (Desktop Version)
  Partition 2 - 1GB Swap

When I start my computer to get into windows I just let it boot up and to get into Ubuntu I press F12 and select to load the IDE drive. This is working fine.

I would like to install VMWare Server and be able to open HD(0,1) my Windows XP MCE installation from within Ubuntu without having to format the partition and reinstall windows. I wont be booting back into windows at any point after doing so as I will just use the VMWare to do everything. What is the best way to do this? Also I noticed while reading other questions similar about when booting up the drive from within VMVare not to select Ubuntu since it could mess up the partition but would this happen since the drive its loading windows from still has the original MBR?

---

### Post by Cypher on 2009-02-18
I think you misunderstand what VMWare is capable of doing. It isn't going to take an existing installation of Windows and make it run within a virtual machine. Rather, you can use the first HD as the storage for WinXP virtual machine, but you'll have to go through SOME sort of installation to make it look/work/behave like your existing WinXP installation.

---

### Post by Demonlord666000 on 2009-02-19
Well VMWare didn't end up working to do that, it was causing BSOD upon loading the other partition's RAW data. But Virtual Box did exactly what I wanted, installed it setup the file to point at my already installed windows XP partition. And booted it up no problem right from with in linux.

---

