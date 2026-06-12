---
title: "second drive installed assumes sda, failed boot"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by jimmy-james on 2009-02-13
I have a weird issue and I am not sure how to solve it so any help would be appreciated.
I tried to install Ubuntu on my computer and I have it set up this way:
HDD1 - 250GB - SATA1
partitions:
windows xp
linux root
linux home
linux swap
programs (for winxp)
unallocated

HDD2 - 500GB - SATA2
partitions
windows xp page disk
data1
data2
data3

I installed ubuntu 8.04 and ran through everything and upon the restart, I got grub errors 17 and 18 I believe.
After some troubleshooting, I unplugged the second HDD (SATA2) and reinstalled the program. Everything worked fine.
After shutting down, I plugged the HDD2 back in and restarted and got a grub error 22

So based upon the drive assignments in the partition editor, the HDD2 is assigned sda and HDD1 is sdb. The original install put grub on HDD2 and the reinstall (with HDD2 unplugged) did it all right putting grub on HDD1 (assigned sda with HDD2 not present).

Make sense?
HDD1 = sda when HDD2 is unplugged
HDD2 = sda when it is plugged in and HDD1 switches to sdb

So my situation now is I have grub on both pointing root to start from sda partition 2.
When both HDs are in, sda(HDD2) has no OS on partition 2 because sda -> sdb and the system stops.
When HD1 only is in, everything is fine but I can't use HDD2
hen I switch cables, computer locks up and graphics scramble after main OS screen.

- How do I wipe GRUB off the MBR of HDD2?
- How do I stop the HDD2 from taking over control of sda or edit GRUB to use sdb's partition 2?

I hope that all made sense. I am lost and feel like I am running in circles. I have also looked in the bios and the hard drives are listed correctly there. SATA1 = HDD1 and SATA2 = HDD2

---

