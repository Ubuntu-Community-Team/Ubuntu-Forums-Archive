---
title: "Uninstall left Ubuntu option on startup"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by greenglen on 2009-10-01
I installed Ubunutu on an XP machine giving the option to boot to XP or Ubuntu at startup. I then uninstalled to reinstall on a laptop instead. Now when I start the XP machine I'm still getting the option to boot in XP or Ubuntu - even though Ubuntu's not there any more. Any way to get rid of this?

---

### Post by random turnip on 2009-10-01
How did you uninstal Ubuntu?

The best way is to boot into the Live CD that you would have used to install Ubuntu.  And use GParted and just edit the partitions on the hard-drive so that XP's partition is taking the whole thing up.  That will totally erase Ubuntu.

---

### Post by greenglen on 2009-10-01
Thanks for the lightning fast response Turnip. I'll go with that method.

---

### Post by SlugSlug on 2009-10-01
> **greenglen said:**
> I installed Ubunutu on an XP machine giving the option to boot to XP or Ubuntu at startup. I then uninstalled to reinstall on a laptop instead. Now when I start the XP machine I'm still getting the option to boot in XP or Ubuntu - even though Ubuntu's not there any more. Any way to get rid of this?

if you boot up your XP disk, drop to recovery mode and type
fixmbr

that will fix it

---

### Post by SlugSlug on 2009-10-01
> **random turnip said:**
> How did you uninstal Ubuntu?

The best way is to boot into the Live CD that you would have used to install Ubuntu.  And use GParted and just edit the partitions on the hard-drive so that XP's partition is taking the whole thing up.  That will totally erase Ubuntu.


that will totaly erase ubuntu but wont get rid of his boot menu

---

### Post by greenglen on 2009-10-01
Thanks Slug, another option to try.

---

### Post by random turnip on 2009-10-01
> **SlugSlug said:**
> wont get rid of his boot menu

Damn, never thought of that.
I actually don't know how to get rid of GRUB.
I would advise Slug's way.

---

### Post by LewRockwell on 2009-10-01
super grub disk will also fix those MBR troubles

.

---

### Post by greenglen on 2009-10-01
Damn, don't have an XP boot disk.

---

### Post by Mark Phelps on 2009-10-01
Hate to point this out, but everyone is answering the wrong question!  All the OP wants to do is remove Ubuntu from the selection menu.

That is done by editing the MS Windows boot.ini file and removing the ONE LINE that refers to the Ubuntu OS.  Make sure you remove only that line.

When you restart, you will probably not even get a boot selection menu anymore because that is only displayed by default when you have more than one selection.

---

### Post by NightwishFan on 2009-10-01
If it is grub:

[LIST=1]
[*]Download supergrub disk.
[*]Burn it as an ISO image.
[*]Reboot with super grub disk in drive.
[*]Run the "Fix boot of windows option".
[/LIST]

[http://prdownload.berlios.de/supergrub/super_grub_disk_0.9798.iso](http://prdownload.berlios.de/supergrub/super_grub_disk_0.9798.iso)

---

### Post by alphaniner on 2009-10-01
> **Mark Phelps said:**
> That is done by editing the MS Windows boot.ini file and removing the ONE LINE that refers to the Ubuntu OS.

Since when have MS boot managers been able to boot into anything other than an MS OS?  Although I do wonder how GRUB could be working if he has really uninstalled Ubuntu.

Still, it seems to me Slug^2 has the right idea.

---

### Post by NightwishFan on 2009-10-01
If he installed using WUBI, it integrates with the Windows Boot loader. If that is the case, then you can delete the Ubuntu option in msconfig. However, if you correctly removed WUBI then it should have already done that.

---

### Post by alphaniner on 2009-10-01
> **NightwishFan said:**
> If he installed using WUBI, it integrates with the Windows Boot loader. If that is the case, then you can delete the Ubuntu option in msconfig. However, if you correctly removed WUBI then it should have already done that.

Aahh, the OP suddenly makes more sense.  The wording did seem a bit unusual.  Thanks.

---

### Post by greenglen on 2009-10-01
Thanks Mark. That's the one.
Thanks to all for suggestions.

---

