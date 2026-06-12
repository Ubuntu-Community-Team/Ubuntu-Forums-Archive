---
title: "Windows 7 + External Hard Drive w/ Linux and Grub."
date: 2010-04-20
forum: New to Ubuntu
---

### Post by Kraust on 2010-04-20
Currently on my Notebook I have Windows 7 Ultimate 32-bit
I have a partition on my External Hard Drive (ext3) that contains BackTrack 4 (No Swap) on a 30GB Partition.

Currently, the only way to boot BT4 is to remove my Notebook's Hard Drive before turning on my Notebook and booting from USB that way. I want to be able to use the Windows Bootloader to Boot Linux from the External Hard Drive.

Is this at all possible? How would I edit Window's Bootloader to do this. I'm not familiar with the new Bootloader but I'm familiar with the fact that Windows 7 does recognize ext3 sometimes (It did when I installed 7 at least. Never since)


~~~~~

I think the Problem lies in the fact that the Partition with Grub (And BackTrack 4) is on the second partition of the Hard Drive. The Main partition is over 450GB (And NTFS) so I wouldn't like to move the main Partiton after the BT4 one. Is there any way I can go around this?

I'm thinking this is the problem as the first time my computer boots from USB it fails causing the root of my problem as it'll boot normally the second time I try (Reasoning on why removing the main HDD works).

---

### Post by Radioman991 on 2010-04-20
Here is what I did on a laptop.....YMMV

POWER OFF LAPTOP

I removed the laptop's hard drive.

POWER ON LAPTOP

Install Linux distro of your choice on my external USB drive.

After install, remove installCD, and make sure BIOS is set to boot form the USB drive before internal HDD.

POWER OFF LAPTOP!

Reinsert laptop HDD.

Now, when I wanted to boot to Windows, just unplug USB drive.  When I wanted to boot into Linux, plug in the external USB drive, restart, and BOOM  booted to USB.

This eliminated accidently clobbering my laptop HDD...which I did once while trying to install onto an external drive.

Hops this helps you accomplish what you want.

---

### Post by Kraust on 2010-04-20
Basically it indeed, but I forgot some important information out of this. It won't do that because Grub is on the second partition of the Hard Drive. Always got to make it harder on myself.

Basically, I alredy new all of that and set the Notebook to boot from USB first while I was waiting for a reply <_<

---

