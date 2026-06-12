---
title: "No Boot selection"
date: 2011-08-28
forum: New to Ubuntu
---

### Post by tcebak on 2011-08-28
Hello, just installed 11.04 with windows 7 already installed.
I set up a 3 & 4 partition, one for the boot loader (FAT32) and the OS on (ext4) when i start the computer i don't have the option to choose which OS to load. did i mess something up? or does the boot loader for unbuntu need to be installed on the same partition as the windows?

Thanks
tony

---

### Post by ExileAmongYou on 2011-08-28
Did you create a separate partition just for the bootloader? I don't think you need to do that, you can install it on your existing partitions, or in the master boot record. Are you holding down shift as the computer boots up? That should bring up the GRUB menu, although it sounds like GRUB doesn't know about your Windows install at the moment.

The quickest fix for this might be to run
```
sudo update-grub2
```
in the terminal. If that doesn't work, you might need to install

---

### Post by tcebak on 2011-09-01
Thank you but the trouble is , I just boot straight into windows seven.  
I have 4 partions first is windows boot loader, second Is windows7, third is set up for ubuntu and 4 is just a small blank space.  It ask me where to place the boot loader and I select the first part ion with the windows loader. The I reformat my 3 partion to install ubuntu on it. 

I've reinstalled a few times and it tells me ubuntu and windows 7 are installed but I just can't load ubuntu. Not even a grub menu

Thanks

---

