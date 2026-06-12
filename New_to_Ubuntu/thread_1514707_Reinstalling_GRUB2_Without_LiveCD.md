---
title: "Reinstalling GRUB2 Without LiveCD?"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by walkerchuckwalker on 2010-06-21
I want to reinstall GRUB2 from the installed version of Ubuntu. I can log into Ubuntu, I just need the commands to either reinstall, update, or revert GRUB.

---

### Post by shawnansasio on 2010-06-21
are you on dual boot. if so doing this might break your other os's bootloader. but if not: sudo aptitude remove grub ?? i think than sudo aptitude install grub

---

### Post by kansasnoob on 2010-06-21
> **walkerchuckwalker said:**
> I want to reinstall GRUB2 from the installed version of Ubuntu. I can log into Ubuntu, I just need the commands to either reinstall, update, or revert GRUB.

You're not very clear about your intended goal. What are you trying to accomplish?

What is grub not doing properly now?

Also, in order to get an idea about your current layout, please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by walkerchuckwalker on 2010-06-21
The intent is to simply just reinstall GRUB2 back to original settings. I can log into Ubuntu and Windows Vista, I just would Like to start over to correct mistakes I have made to some files.

---

### Post by drs305 on 2010-06-21
The 'nuclear' option would be to uninstall and reinstall grub-common and grub-pc. The following commands would remove them both and then reinstall them both (because of dependencies, both packages needn't be listed in the commands). *While running a normal installation:*

Since there will be a short period when you have *no* bootloader, make sure you have a reliable internet connection and power source.

You will be warned about removing the bootloader. During the install, you will be given the chance to first add options to the kernel boot process. Normally you can just TAB to "OK" and press ENTER.

Next you will be asked on which drive(s)/partition(s) you want. Use the UP/DN arrows, the spacebar to select, and TAB to "OK" when you are done. You normally only want to select the DRIVE (for instance, sda) and NOT a partition.

```
sudo apt-get update
sudo apt-get purge grub-common
sudo apt-get install grub-pc
```

---

