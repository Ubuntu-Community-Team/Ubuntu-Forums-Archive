---
title: "sd card reader"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by degarb on 2010-02-22
I have a sd card reader which works on every xp computer in house.  But I plug it and a card into the usb in ubuntu and nothing.   I looked in >filesystem>media too.

---

### Post by beckx020 on 2010-02-22
I believe you have to have an SD card in the slot when you boot for it to recognize them.

---

### Post by Ozymandias_117 on 2010-02-22
Can you put the card reader in, with a card, and post the results of "sudo lsusb" and "sudo fdisk -l"

---

### Post by degarb on 2010-02-22
> **Ozymandias_117 said:**
> Can you put the card reader in, with a card, and post the results of "sudo lsusb" and "sudo fdisk -l"

I just rebooted.   now it shows a generic card reader in places computer (not media).  But i cannot open it.

lsusb:
Bus 001 Device 002: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  

 sudo fdisk -l

Disk /dev/sda: 6007 MB, 6007357440 bytes
255 heads, 63 sectors/track, 730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d6ff4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         692     5558458+  83  Linux
/dev/sda2             693         730      305235    5  Extended
/dev/sda5             693         730      305203+  82  Linux swap / Solaris

---

### Post by degarb on 2010-02-22
in places computer (not media)  edited

---

