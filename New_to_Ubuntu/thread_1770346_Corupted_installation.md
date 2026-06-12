---
title: "Corupted installation"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by Tonanti216 on 2011-05-29
I installed Ubuntu 9.04 some time ago and then after some initial use left it alone and have only just gone back to using it.  However, I managed somehow to corrupt the installation and now can't access the applciations through the menus and generally have lost my way and seem to have 2 differing "accounts" on my PC.  I installed Ubuntu "inside windows" and dual boot.  I want to remove Ubuntu all together, remove the partition and start over but I am finding the mass of information available somewhat muddled and confusing.  Can anyone give me some clear and simple pointers on what I can and cannot do.  I simply wish to get the installation sorted and then reinstall the latest version of Ubuntu and start over.  So, anyone able to guide me ? Can I just remove the partition and delete all Ubuntu program files on my C drive or is there far far more to it?
Many thanks.

Oh, I am using Windows XP and there is no Ubuntu listed in my Add/Remove Programs listing.

---

### Post by drpjkurian on 2011-05-29
Boot the machine from  ubuntu live cd. open the programme 'gparted' which is listed in 'preferences'.
Format the partition in which Older ubuntu is installed and do the new installation from the live cd

---

### Post by sanderd17 on 2011-05-29
If you installed it in Windows (with wubi) it's easy, just boot into windows and go toe add/remove software, there you can uninstall ubuntu.

If you try to delete files manually, it is possible that ubuntu isn't uninstallable anymore.

[s]@drpjkurian: it's installed with wubi: so it isn't on a separate partition.[/s]

EDIT: are you sure it's installed inside windows? please run the boot info script: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Tonanti216 on 2011-05-29
> **sanderd17 said:**
> If you installed it in Windows (with wubi) it's easy, just boot into windows and go toe add/remove software, there you can uninstall ubuntu.

If you try to delete files manually, it is possible that ubuntu isn't uninstallable anymore.

[s]@drpjkurian: it's installed with wubi: so it isn't on a separate partition.[/s]

EDIT: are you sure it's installed inside windows? please run the boot info script: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
O, got that. BUT, Ubuntu isn't listed in the Add/remove software list.  I already tried to do that.  Yes, I dual boot to Ubuntu and it has it's own partition in Windows.  

Can I simply delete the Partition with EasyBCD or diskmgmt.msc in Windows?

---

### Post by Tonanti216 on 2011-05-29
> **drpjkurian said:**
> Boot the machine from  ubuntu live cd. open the programme 'gparted' which is listed in 'preferences'.
Format the partition in which Older ubuntu is installed and do the new installation from the live cdWil that simply override the existing partition if I do that?  or do I have to remove the partition and then do a fresh install?

---

### Post by sanderd17 on 2011-05-29
In the installation, you can choose the manual mode, there you can select the partition where your current ubuntu is installed. So it will format that and install the new ubuntu there.

GRUB will be reinstalled, so you don't have to worry about those settings.

You could off coarse first delete the old ubuntu partition with gparted, but that just seems extra work to me.

---

### Post by Tonanti216 on 2011-05-29
> **sanderd17 said:**
> In the installation, you can choose the manual mode, there you can select the partition where your current ubuntu is installed. So it will format that and install the new ubuntu there.

GRUB will be reinstalled, so you don't have to worry about those settings.

You could off coarse first delete the old ubuntu partition with gparted, but that just seems extra work to me.
OK, this sounds good to me ... I will give this a try - Thank you.

---

