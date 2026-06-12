---
title: "New Dell w/Win11 want to add/replace with Ubuntu 22.04.02"
date: 2024-03-28
forum: Networking &amp; Wireless
---

### Post by ricknesti on 2024-03-28
Dell inspiron 15 3525 64gb RAM 64-BIT OS AMD PROCESSOR  1TB 
WIN HOME 11 OS

I Would like to add UBUNTU or just put UBUNTU only OS.  

Cannot get the boot menu to run install USB...any help?

thx for any assistance!!!

rn

PS.11:07PM I Have to call it night will check back at 7:30am

---

### Post by him610 on 2024-03-28
You may need to go into the Bios/Euve setup, find where boot priority is, and set it to the USB device where Ubuntu installation files reside.
You should refer to your motherboard manual before you attempt anything.
Another option, remove and replace original DiskDrive (DD) with new pristine DD.

---

### Post by ricknesti on 2024-03-29
him610,
Thx for the feedback, I can change boot priority but this probably the limit of my ability.  
~Regards

---

### Post by oldfred on 2024-03-29
I have a Dell 3510 with Intel.
Kubuntu 22.04 just installed, I even forgot to make all the suggested changes that I have told others to make.
But I believe booting Windows made sure UEFI firmware & NVMe drive's firmware were updated.
sudodus -In a Dell Latitude 3520 Windows is installed with RST, and installed Ubuntu 22.04 LTS alongside it without changing any setting in the UEFI/BIOS system.
[https://askubuntu.com/questions/1411848/nvme-vs-ahci-speed-when-trying-to-install-ubuntu](https://askubuntu.com/questions/1411848/nvme-vs-ahci-speed-when-trying-to-install-ubuntu)
[https://ubuntuforums.org/showthread.php?t=1543006&p=14097006#post14097006](https://ubuntuforums.org/showthread.php?t=1543006&p=14097006#post14097006)

Do not know if Intel VMD driver for RAID works with AMD systems.
Normally we have suggested turning RAID off and changing to AHCI. But if dual booting with Windows you have to install AHCI drivers for it to boot.
Dell 15 Inspiron 3000 RST & bitlocker off
[https://ubuntuforums.org/showthread.php?t=2469456](https://ubuntuforums.org/showthread.php?t=2469456)
Dell  Inspiron 3670 UEFI update & AHCI worked
[https://ubuntuforums.org/showthread.php?t=2412152](https://ubuntuforums.org/showthread.php?t=2412152)

You also need Windows fast startup/hibernation off and bitlocker off for the Linux NTFS driver to see the existing partitions.

Some general UEFI install instructions (and more links) in link below in my signature.

---

### Post by ricknesti on 2024-03-30
Oldfred, 

Thank you for the feedback and links and I will work through these links and their content.  Wil report back after easter. 
~Regards

---

