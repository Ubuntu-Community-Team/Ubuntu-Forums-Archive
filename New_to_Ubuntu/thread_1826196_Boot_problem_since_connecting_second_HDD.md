---
title: "Boot problem since connecting second HDD"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by popffabrik on 2011-08-16
Hi, I have Linux 11.04 installed, as well as Windows 7 (I installed Windows 7 after Ubuntu). Both are installed on one HDD, on different partitions. Boot was working fine, I got a boot menu where I could choose Ubuntu or Windows 7.

Today I connected a second HDD, since then it gives me the error, right after the Motherboard screen:

error: no such device: Could not find device "..." (a long array of letters and numbers).
grub rescue>

What can I do?

Thanks!

---

### Post by Bucky Ball on 2011-08-16
External? If so, make sure it is switched off when you boot, then you can at least boot and makes some changes.

---

### Post by popffabrik on 2011-08-16
No it's internal. My main HDD, on which ubuntu and win7 are installed, is a

Samsung HD103SJ Spinpoint F3 1TB Hard Drive SATAII 7200rpm 32MB Cache - OEM.

My second HDD is a

Hitachi ATA/IDE 400GB.

---

### Post by corncob on 2011-08-16
> **popffabrik said:**
> No it's internal. My main HDD, on which ubuntu and win7 are installed, is a

Samsung HD103SJ Spinpoint F3 1TB Hard Drive SATAII 7200rpm 32MB Cache - OEM.

My second HDD is a

Hitachi ATA/IDE 400GB.

Welcome to the forums!  I never tried to use a SATA and IDE drive together.  There is a jumper on the IDE drive with positions for Master, Single Drive, Slave, or Cable Select.  I might think that if its set for Master or Single Drive it might screw things up.  If so, try setting it for Slave, or Cable Select if you have a CS cable (80 wire or Master and Slave printed on the terminals.

---

### Post by oldfred on 2011-08-16
When you have both SATA & PATA, many BIOS promote the PATA drive to sda or hd0 or drive0, but your boot is on the SATA drive. 

Can you set in BIOS to boot the SATA. Ubuntu should boot (as long as you are using UUID not device names), but windows may need repairs as it has settings looking for drive0 and it is now drive1.

---

