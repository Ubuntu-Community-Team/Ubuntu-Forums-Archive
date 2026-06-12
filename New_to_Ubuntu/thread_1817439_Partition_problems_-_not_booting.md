---
title: "Partition problems - not booting"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by getut on 2011-08-03
I am having a Kubuntu natty 64 bit partitioning issue. I'm not an utter newbie to Ubuntu/Kubuntu/Linux but the way I have always done it is not working on this machine.

I am installing it on a new HP small form factor Core I7 based machine and I typically put Home on its own partition. For example, in this case I am choosing a 30GB SDA1 EXT4 mounted as /, a 205GB SDA2 mounted as home, and a 5GB swap area. Other than size differenced I have done at least 30-40 linux installs using this exact same layout.

On this particular machine, it won't boot if I do that. If I choose the Guided - use the whole disk option, this machine winds up with a 20GB EFI partition which is something I have never seen before when choosing use the whole disk. It usually makes 1 large partition for everything other than swap and then makes a swap partition for 2 partitions total. Guided - use the whole disk is making 3 on this machine and it boots properly when it does it.

What is going on? How can I get a separate boot partition like I want? What is the EFI partition and is it required?

---

### Post by amjjawad on 2011-08-03
[http://en.wikipedia.org/wiki/EFI_System_partition](http://en.wikipedia.org/wiki/EFI_System_partition)

---

### Post by oldfred on 2011-08-03
Most of the very new systems use UEFI even if they only mention BIOS, they often have a BIOS compatible mode also. 

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB. Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)

---

### Post by srs5694 on 2011-08-04
As oldfred says, when booting in UEFI mode, you need an EFI System Partition (ESP), which the installer creates in its auto-partitioning mode. (You probably meant that it's 20 MB, not 20 GB. A typical size for an ESP is in the 100-200 MB range, but Ubuntu creates them on the small side.) The ESP holds (U)EFI boot loaders and related data for the firmware. If you use the ELILO boot loader, the Linux kernel normally goes in the ESP, which is impossible with the dinky little ESP that Ubuntu creates; thus, I recommend an ESP of ~200-250 MB so that you've got the option of switching to ELILO should that become desirable. The use of the ESP breaks the reliance on code tucked away in the MBR, in the boot partition's boot sector, and in unpartitioned parts of the disk that you find on BIOS-based computers.

If you care to re-install, you should be sure to create an ESP yourself and also identify it as an "EFI boot partition" (or similar not-quite-standard name) in the partition setup screen. Alternatively, you could start with what you've got, shrink your existing partition, and create a new partition to serve as /home.

---

### Post by getut on 2011-08-05
Thanks for the information guys.. That got it! Marking solved.

---

