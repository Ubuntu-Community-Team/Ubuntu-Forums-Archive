---
title: "Grub loader doesnt reflect /boot/grub/menu.lst"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by Explor on 2011-04-30
Hi All,

I am new so excuse me if this has been discussed before. I tried looking around but cannot find a solution.

My /boot/grub/menu.lst is updated after I upgraded to Ubuntu 11.04. But the boot loader shows me my previous linux kernels 2.6.35-22 instead of 2.6.38-8. I have used the command sudo update-grub to regenerate grub but it doesnt reflect in my boot loader. I have uploaded my /boot/grub/menu.lst here. Please advice

Thanks
Anil

---

### Post by falko on 2011-04-30
The GRUB configuration can be found in the /etc/grub.d/ directory.

---

### Post by alphacrucis2 on 2011-04-30
> **Explor said:**
> Hi All,

I am new so excuse me if this has been discussed before. I tried looking around but cannot find a solution.

My /boot/grub/menu.lst is updated after I upgraded to Ubuntu 11.04. But the boot loader shows me my previous linux kernels 2.6.35-22 instead of 2.6.38-8. I have used the command sudo update-grub to regenerate grub but it doesnt reflect in my boot loader. I have uploaded my /boot/grub/menu.lst here. Please advice

Thanks
Anil

Grub2 doesn't use menu.lst. Maybe the upgrade replaced grub with grub2. I think grub2 has been default for the last few releases but I recall an upgrade in place didn't normally upgrade grub to grub2. Maybe that has changed?

---

### Post by grahammechanical on 2011-04-30
I would like to understand clearly the problem. Are you saying that the Grub menu does not show the line?

> Ubuntu 11.04, kernel 2.6.38-8-generic

How many partitions and installations do you have? I have more than one version of Ubuntu installed and each partition has a copy of the Grub configuration files. It could be that Grub is not booting from the menu list that you are posted but from another menu list on another partition that has not been updated to recognize the 11.04 kernel.

I am just trying to think of something, anything.

regards.

---

### Post by Explor on 2011-04-30
alphacrucis2 : Maybe you are right. How do I update grub2 then to get the latest linux kernel listed in there?

grahammechanical: I have 3 partitions 1 ext3 and 2 ntfs. I have ubuntu and XP installed. 

Also one thing I need to clarify is that the inability to update grub is not because of upgrade to 11.04. The problem was there before as well. After 2.6.36 there had been updates to the kernel, which I installed but my grub loader would never show those options. 

Thanks for ur replies guys.

---

### Post by alphacrucis2 on 2011-04-30
> **Explor said:**
> alphacrucis2 : Maybe you are right. How do I update grub2 then to get the latest linux kernel listed in there?

grahammechanical: I have 3 partitions 1 ext3 and 2 ntfs. I have ubuntu and XP installed. 

Also one thing I need to clarify is that the inability to update grub is not because of upgrade to 11.04. The problem was there before as well. After 2.6.36 there had been updates to the kernel, which I installed but my grub loader would never show those options. 

Thanks for ur replies guys.

Documentation on grub2 may help:

[URL="https://help.ubuntu.com/community/Grub2"]https://help.ubuntu.com/community/Grub2

[/URL]

---

### Post by Explor on 2011-04-30
I just found out that I have legacy grub or grub version 0.97. 

the file /boot/grub/grub.cfg contents is what is exactly reflected in the bootloader and not the content of file /boot/grub/menu.lst.. 

now what should I do that changes the file grub.cfg?

---

### Post by oldfred on 2011-04-30
It seems like you are booting with grub2, but the update-grub is updating menu.lst from old grub legacy. You need to cleanly uninstall both and just reinstall grub2. Note that while both are uninstalled you will not be able to reboot and the reinstall requires a working internet connection to download the new copy of grub2.

# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda
sudo update-grub

This includes chroot in case you have to do it from LiveCD, but shows above commands with more detail.
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Explor on 2011-04-30
Before I could read the previous reply I installed grub2 all over again without uninstalling grub legacy or previous grub2. Because of this when I restarted my system the boot loader wouldnt load and gave grub_env_export error. Hence I had to reinstall grub2 from liveCD to clean up the mess. 

I used this link and it solved my problem... 
[https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT](https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT)

Thanks for those replied!
Anil

---

