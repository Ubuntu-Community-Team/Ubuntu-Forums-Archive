---
title: "Boot screen"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by itsvan on 2009-10-11
I have a pondering...on my boot screen there used to show up only the Ubuntu options and the windows option to boot.

after doing an update on Jaunty now all the ubuntu options are repeated on the boot menu....what does this mean? is it taking more space than it should or it doesnt matter?

---

### Post by LewRockwell on 2009-10-11
> **itsvan said:**
> I have a pondering...on my boot screen there used to show up only the Ubuntu options and the windows option to boot.

after doing an update on Jaunty now all the ubuntu options are repeated on the boot menu....what does this mean? is it taking more space than it should or it doesnt matter?

that is due to additional kernels being added

you can edit the /boot/grub/menu.lst file to make your boot menu look the way you want it to

.

---

### Post by mcduck on 2009-10-11
> **itsvan said:**
> I have a pondering...on my boot screen there used to show up only the Ubuntu options and the windows option to boot.

after doing an update on Jaunty now all the ubuntu options are repeated on the boot menu....what does this mean? is it taking more space than it should or it doesnt matter?

When the kernel is updated the new version won't replace the old once, instead it's installed alongside with the old one. This allows you to boot using the old version if, for some reason, the new one doesn't work correctly on your computer.

The extra kernel versions do take some disk space, but it definitely doesn't mean that your Ubuntu install would now take twice the disk space or anything like that, kernel and all related packages take couple of hundred megabytes on your disk.

Most people prefer keeping at least one older kernel version available all the times, but you can actually install the old versions safely once you have confirmed that everything works fine with the latest version. Simply uninstalling the old kernel version's packages with Synaptic Package Manager will automatically remove it from the Grub menu as well. 

Alternatively the easy way is to use System/Administration/Computer Janitor, which will keep one older kernel available and offer to remove any others.

(I wouldn't recommend editing the menu.lst, since that's just a cosmetic change and won't actually free any disk space for you.)

---

