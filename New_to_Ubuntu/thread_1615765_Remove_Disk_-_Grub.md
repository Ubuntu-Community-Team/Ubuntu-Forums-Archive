---
title: "Remove Disk - Grub"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by jkurtisr32 on 2010-11-07
Hi,

I recently Installed Ubuntu on a second HDD on my system. The original intention was to remove this HDD after the install and put it in another computer.

We'll, I forgot about the boot loader, and I think that my primary boot partition picked up the presence of the other drive. Now if I remove the additional drive, the original will not boot. Is there a way for me to remove this second drive from the bootloader's expectations?

I've looked around at several places that offer Grub help, but no solutions are specific to this issue. I was thinking about just uninstalling/reinstalling Grub, but I didn't want to mess with anything without asking about if first.

All help is appreciated.

Thanks,
Kurt

---

### Post by kansasnoob on 2010-11-07
> **jkurtisr32 said:**
> Hi,

I recently Installed Ubuntu on a second HDD on my system. The original intention was to remove this HDD after the install and put it in another computer.

We'll, I forgot about the boot loader, and I think that my primary boot partition picked up the presence of the other drive. Now if I remove the additional drive, the original will not boot. Is there a way for me to remove this second drive from the bootloader's expectations?

I've looked around at several places that offer Grub help, but no solutions are specific to this issue. I was thinking about just uninstalling/reinstalling Grub, but I didn't want to mess with anything without asking about if first.

All help is appreciated.

Thanks,
Kurt

With both drives installed boot into the new installation and post the results of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternative instructions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by drs305 on 2010-11-07
If you boot to your normal drive's Ubuntu, you can reinstall Grub2 in that drive's MBR with the following command. The command assumes your normal drive with Ubuntu is sda and the one you want to get rid of is not sda.
```
sudo grub-install /dev/sda
sudo update-grub
```

That will put the bootloader back on sda and point to your current install's Ubuntu partition.  If you don't want to have the second drive's listings in the Grub menu at all, remove the second drive or disable /etc/grub.d/30_osprober (remove the executable bit) before running "update-grub".

Edit: Simultaneous post with *kansasnoob*. If you have questions about what to do run the boot info script and post as he requested.

---

### Post by kansasnoob on 2010-11-07
> **drs305 said:**
> If you boot to your normal drive's Ubuntu, you can reinstall Grub2 in that drive's MBR with the following command. The command assumes your normal drive with Ubuntu is sda and the one you want to get rid of is not sda.
```
sudo grub-install /dev/sda
sudo update-grub
```

That will put the bootloader back on sda and point to your current install's Ubuntu partition.  If you don't want to have the second drive's listings in the Grub menu at all, remove the second drive or disable /etc/grub.d/30_osprober (remove the executable bit) before running "update-grub".

Edit: Simultaneous post with *kansasnoob*. If you have questions about what to do run the boot info script and post as he requested.

I was unsure what OS's might even be installed in the old drive so I opted for info first :)

---

### Post by jkurtisr32 on 2010-11-08
> **kansasnoob said:**
> I was unsure what OS's might even be installed in the old drive so I opted for info first :)

I believe that the original Ubuntu drive is sda by default, but I will double check. It is the only physical drive that I keep in that machine, but it contains both Ubuntu and Win7.

---

### Post by jkurtisr32 on 2010-11-10
> **drs305 said:**
> If you boot to your normal drive's Ubuntu, you can reinstall Grub2 in that drive's MBR with the following command. The command assumes your normal drive with Ubuntu is sda and the one you want to get rid of is not sda.
```
sudo grub-install /dev/sda
sudo update-grub
```

That will put the bootloader back on sda and point to your current install's Ubuntu partition.  If you don't want to have the second drive's listings in the Grub menu at all, remove the second drive or disable /etc/grub.d/30_osprober (remove the executable bit) before running "update-grub".

Edit: Simultaneous post with *kansasnoob*. If you have questions about what to do run the boot info script and post as he requested.

This worked well for me. Thanks a lot for your help.

-Kurtis

---

