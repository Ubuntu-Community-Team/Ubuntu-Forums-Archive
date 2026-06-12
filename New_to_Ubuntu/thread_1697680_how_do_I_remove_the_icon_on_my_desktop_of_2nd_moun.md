---
title: "how do I remove the icon on my desktop of 2nd mounted HD?"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-03-01
Hi Ubuntu Community:

I have a second hard drive, /dev/sdb1

I mount it automatically using /etc/fstab

The line in /etc/fstab that mounts the drive is:

/dev/sdb1    /media/WIDSOM   ext4    defaults     0        2

An icon of that hard drive shows up on my desktop... see the upper right hand corner of the attachment (those are my sons in the picture).

I do not want that icon to show on my desktop because it can accidentally be unmounted.

How do I get that icon to vanish without unmounting the device?

Thanks,
Phil Smith
DUluth, GA

---

### Post by YesWeCan on 2011-03-01
The automatic desktop icon is particular to /media. Just mount the drive somewhere else, such as /mnt.

---

### Post by pressko on 2011-03-01
HI , 

Or just install ubuntu tweak and there is an option on desktop section : Do not show mounted device on desktop . Mark it and u are done :)

---

### Post by mcduck on 2011-03-01
> **pressko said:**
> HI , 

Or just install ubuntu tweak and there is an option on desktop section : Do not show mounted device on desktop . Mark it and u are done :)

Of course you don't need Ubuntu Tweak to do that (the option is in gconf-editor, which is installed by default) and doing that will not only hide the single selected drive, but instead *all drives, removable drives/devices and optical media*.

If you just want to avoid getting a desktop icon for a particular drive, then mounting it anywhere else than in /media is the best way.

---

### Post by Old Jimma on 2011-03-01
Thank you!

---

