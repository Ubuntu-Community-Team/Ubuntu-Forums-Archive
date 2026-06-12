---
title: "Clean Up Ubuntu Grub Boot Menu After Upgrades"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by amityadav9314 on 2010-07-23
hi there!
well i had tried to clean up my grub boot menu but when i tried this command ...gksu gedit /boot/grub/menu.lst...it shows a blank file of gedit...
i tried to do it by using the help of followin  link...


h**p://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/

i don't understand why my gedit menu.lst file is empty.
help me...

---

### Post by DrMelon on 2010-07-23
GRUB is now depreciated: the later versions of Ubuntu use GRUB2, and GRUB2 does not use a menu.lst.

[http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)

---

### Post by Elfy on 2010-07-23
menu.lst is for grub legacy. It's likely that you have grub2.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

What do you mean by clean up?

---

### Post by drs305 on 2010-07-23
You can eliminate Recovery Mode & memtest86+ entries via settings in /etc/default/grub.

You can remove older kernel references on your current / partition by removing them. I've found the simplest method is via Ubuntu-Tweak, which has a nice GUI interface. See the section "Removing older kernels" in this link: [http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

Grub2 will also 'mine' data from other partitions - getting kernels and menu entries from old grub legacy menu.lst files, among others; you may find references to other kernels even after removing the ones on your current system partition.

If you clean up your menu and still have entries you can't seem to get rid of, let us know. At that point, providing the contents of */boot/grub/grub.cfg* would be helpful.

In addition to the link provided in the previous post, you can also learn about Grub 2 via the links in my signature line.

---

### Post by emoguitarist06 on 2010-07-23
> **drs305 said:**
> 
You can remove older kernel references on your current / partition by removing them. I've found the simplest method is via Ubuntu-Tweak, which has a nice GUI interface. See the section "Removing older kernels" in this link: [http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")



I second Ubuntu Tweak!
Or you can remove the linux-header entries in synaptic package manager

---

### Post by dryphi on 2011-01-11
From what I've read, Grub2 supposedly automatically removes old kernal entries from the boot menu when the package is removed.

I say supposedly because I recently tried this. After I last updated the kernal version went to 2.6.35-24. After a reboot I removed the 2.6.35-22 packages from Synaptic, and yet the kernal entries are still in my boot menu.
What gives?

Edit: I downloaded Grub Customizer to address this problem and it works like a charm. Still I am curious why Grub2 is not automatically updating.

---

### Post by Quackers on 2011-01-11
> **dryphi said:**
> From what I've read, Grub2 supposedly automatically removes old kernal entries from the boot menu when the package is removed.

I say supposedly because I recently tried this. After I last updated the kernal version went to 2.6.35-24. After a reboot I removed the 2.6.35-22 packages from Synaptic, and yet the kernal entries are still in my boot menu.
What gives?

Edit: I downloaded Grub Customizer to address this problem and it works like a charm. Still I am curious why Grub2 is not automatically updating.

Have you run ```
sudo update-grub
``` since?

---

### Post by drs305 on 2011-01-11
> **dryphi said:**
> From what I've read, Grub2 supposedly automatically removes old kernal entries from the boot menu when the package is removed.

I say supposedly because I recently tried this. After I last updated the kernal version went to 2.6.35-24. After a reboot I removed the 2.6.35-22 packages from Synaptic, and yet the kernal entries are still in my boot menu.
What gives?

If all the components of the kernel are removed it should be removed from the menu. 

First you can inspect the /boot/grub/grub.cfg file and find in which section the offending kernel menuentry resides. If it is in the #10_linux section G2 is finding the kernel in your current OS's partition. 

If it's in 30_os-prober it means the kernel is located in another partition or still mentioned in another OS's grub.cfg, menu.lst or grub.conf.

Don't forget it won't be removed from any custom menus you have created.

I use [Ubuntu Tweak]("http://ubuntuforums.org/showthread.php?t=1587462") to remove kernels; it's thorough and easy to use. I can't remember if G2 picks up linux headers but I'm thinking that at least a few users have reported in the past that the kernel remains until the headers are removed.

And of course you have to run "sudo udpate-grub".

---

### Post by dryphi on 2011-01-12
No I didn't run sudo update-grub afterwards, but I did now, and it still says:
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Listed along with the more current version, although the "-22" version packages are not installed in Synaptic.

Also I have since removed them from the boot menu with Grub Customizer, but I'd still like to figure out a better solution.

Thanks.

---

### Post by dryphi on 2011-01-12
> **drs305 said:**
> If it is in the #10_linux section G2 is finding the kernel in your current OS's partition.

Yes it is in the #11_linux section

---

### Post by dryphi on 2011-01-12
There it goes. I used Ubuntu Tweak like you said. Love it.
Thanks

---

