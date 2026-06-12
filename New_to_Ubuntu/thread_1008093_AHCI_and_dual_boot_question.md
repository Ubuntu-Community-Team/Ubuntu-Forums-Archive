---
title: "AHCI and dual boot question"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by Falc7 on 2008-12-11
I am going to install XP, but i was having some problems apparently because i needed to disable AHCI or add a driver for it, is that safe to do considering that i already have ubuntu installed on the HD?

---

### Post by logos34 on 2008-12-11
yes its safe to do that.  Vista has native support for ahci, but not XP, which runs sata drives in IDE legacy/emulation compatibility mode, so you'll have to switch it each time because ubuntu was installed with ahci enabled

---

### Post by bumanie on 2008-12-11
There should not be any issue with that as they will be on different partitions. However installing windows as the second OS will overwrite grub and you will have to reinstall grub via a live cd and probably also edit your /boot/grub/menu.lst to include windows.

---

### Post by logos34 on 2008-12-11
> **bumanie said:**
>  installing windows as the second OS will overwrite grub and you will have to reinstall grub via a live cd and probably also edit your /boot/grub/menu.lst to include windows.

yep, forgot to add that--see link in my signature.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu)

You can also automatically add windows to fstab:

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by lametike on 2008-12-11
i thought the best way is to install windows xp first then install ubuntu....that works for me ><.

---

### Post by Falc7 on 2008-12-11
> **logos34 said:**
> yes its safe to do that.  Vista has native support for ahci, but not XP, which runs sata drives in IDE legacy/emulation compatibility mode, so you'll have to switch it each time because ubuntu was installed with ahci enabled

What do you mean when you say 'switch it'? Is it difficult to switch it? If so it sounds like it would be better to completely wipe ubuntu, get Xp first, then reinstall ubuntu. Unless ofc switching is easy.

---

### Post by Paqman on 2008-12-11
Once you have XP installed you can install SATA drivers for it anyway (I believe they're included in one of the Service Packs?). After that you can switch the BIOS back to AHCI.

---

### Post by Falc7 on 2008-12-11
ah good, so i won't need to change anything in the bios every time i want to switch between ubuntu and XP, that was what i was worried about

---

### Post by logos34 on 2008-12-11
yeah, once xp is installed you could use something like nLite to slipstream the sata drivers into a custom install cd.  Or else put them on floppy and insert them during install (F6) like you would RAID drivers

---

### Post by Falc7 on 2008-12-14
I have installed XP, by slipstreaming this driver in:
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=2101&DwnldID=17061&strOSs=45&OSFullName=Windows*%20XP%20Home%20Edition&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=2101&DwnldID=17061&strOSs=45&OSFullName=Windows*%20XP%20Home%20Edition&lang=eng)


How do i switch the BIOS back to AHCI? I pressed F2 at system start up but i don't see any options there

---

### Post by logos34 on 2008-12-14
your motherboard manual will tell you exactly what section its under. google it

---

### Post by Falc7 on 2008-12-14
AHCI is back on :-)

---

