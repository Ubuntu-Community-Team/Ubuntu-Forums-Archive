---
title: "Looking for advice on new build dual boot"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by wanderingarticfox on 2009-03-31
I'm new so first hello everyone. I've been studying and researching for my first build slated for this summer. I am waiting for my Ubuntu CD and there is plenty of time. However I am in a bit of a pickel with the options for my new system HDD set up and instal for multi-boot options. I understand that Ubuntu comes with GRUB and that sounds great:) I plan to instal XP Pro 32-bit first. Q:should I partition at that time and only format the XP volume or should I wait to repartition when installing Ubuntu/GRUB. Also I am not quite clear on if the swap file is to be FAT32 or the entire XP instal should be FAT32??

On another issue is that of AMD and ATI firmware and drivers. The motherboard I will use is a Gigabyte GA-MA790GP-UD4H with 
  AMD 790GX north bridge 128MB DDR3 sideport RAM
  AMD 750 south bridge
  ATI HD3300 intergrated graphics
  AMD OverDrive
  Gigabyte EasyTune6
  Phenom II X3 720 cpu
  2 x 2GB PC2 8500 RAM
  640 or 750 GB Western Digital  Caviar Black SATAII HDD
Q: does anyone know of any issues with these components or features that I should be awaire of heading into this build with the dual boot or possibly multi-boot [some more buntu:)] that maybe I can learn about before late summer? I have been reading the community and knowledge based information for about two weeks but have noticed some issues at a different forum concerning the ATI drivers. Thank you for reading and all answers are welcome; gotta stay on the learning curve don't ya know](*,)

---

### Post by leonardo_neo on 2009-03-31
> Q:should I partition at that time and only format the XP volume or should I wait to repartition when installing Ubuntu/GRUB. Also I am not quite clear on if the swap file is to be FAT32 or the entire XP instal should be FAT32??


You don't have to touch your Xp partition. When you will get your Ubuntu live CD, just insert it, and try your live CD first (without installation). That will also let you know if there is any compatibility issue with your hardwares.

If all goes good, then install Ubuntu. While installation, it will create it's own partition. Your Xp partition will remain intact. You don't have to worry for file system of swap, you just have to select 'swap' while installing ubuntu. Again you don't have to touch your Xp partition, so even if it is NTFS, there is no problem, Ubuntu can access that.

Read this link on how to install Ubuntu.

> [https://help.ubuntu.com/8.04/switching/installing.html](https://help.ubuntu.com/8.04/switching/installing.html)

---

### Post by DJonsson2008 on 2009-04-03
Hard drives are cheap enough these days, you might consider some kind of dual HD system over a dual boot system.

I had a dual boot XP/Ubuntu system here and it was a major headache,
you should scan all the issues people have with dual boot before deciding if that is really what you want to get into.

For my initial tests of Ubuntu I used flea marked HDs, I've since
has upgraded, but even new decent HDs are so cheap enough these days,
it makes me wonder why anyone tweaks with dual boot.

My bios on this machine includes a boot selector which makes it easy.
I've also used drive drawers to the same effect.

---

### Post by wanderingarticfox on 2009-04-04
Well if not dual boot maybe VMware???? I looked around at their site but I'm not sure if the system req's are not up to date. Their Workstation 6.5 does not list Phenom or Phenom II tri or quad cores they just mention multi CPU's which I'm not building. 
Anyone using VM with a 64bit Windows Host and 32 and/or 64 bit Ubuntu with a multi-core AMD or Intel ????:-k

---

### Post by presence1960 on 2009-04-04
> **wanderingarticfox said:**
> I'm new so first hello everyone. I've been studying and researching for my first build slated for this summer. I am waiting for my Ubuntu CD and there is plenty of time. However I am in a bit of a pickel with the options for my new system HDD set up and instal for multi-boot options. I understand that Ubuntu comes with GRUB and that sounds great:) I plan to instal XP Pro 32-bit first. Q:should I partition at that time and only format the XP volume or should I wait to repartition when installing Ubuntu/GRUB. Also I am not quite clear on if the swap file is to be FAT32 or the entire XP instal should be FAT32??

On another issue is that of AMD and ATI firmware and drivers. The motherboard I will use is a Gigabyte GA-MA790GP-UD4H with 
  AMD 790GX north bridge 128MB DDR3 sideport RAM
  AMD 750 south bridge
  ATI HD3300 intergrated graphics
  AMD OverDrive
  Gigabyte EasyTune6
  Phenom II X3 720 cpu
  2 x 2GB PC2 8500 RAM
  640 or 750 GB Western Digital  Caviar Black SATAII HDD
Q: does anyone know of any issues with these components or features that I should be awaire of heading into this build with the dual boot or possibly multi-boot [some more buntu:)] that maybe I can learn about before late summer? I have been reading the community and knowledge based information for about two weeks but have noticed some issues at a different forum concerning the ATI drivers. Thank you for reading and all answers are welcome; gotta stay on the learning curve don't ya know](*,)
Don't be thrown off- a dual boot is more tricky then installing one OS, but not that difficult to do especially with the help you will get in here.

Since you are doing a new build I would partition first from the Ubuntu Live CD or gparted Live CD. Then install Windows first. This will save you having to defrag Windows prior to installing Ubuntu. Also if you install Windows after Ubuntu on the same HDD your GRUB will be wiped and have to be restored (not a hard thing to do). Once Windows is installed on it's partition, pop in the Ubuntu Live CD and install Ubuntu.

---

### Post by rizzeh on 2009-04-04
always try to use separate hard drives for dual boot, makes things SO much easier

---

