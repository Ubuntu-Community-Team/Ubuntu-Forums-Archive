---
title: "sys settings/sharing/samba uncheck readonly not sticking"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by AxMstrLP on 2008-06-07
I've recently installed kubuntu 8.04 after running gentoo for a few years.  I'm really used to command line administration of linux things.  Admittedly I'm new to KDE, though I'm pretty sure this is a bug...

I've been trying to share my home directories for the other windows boxes in the house.  smb.conf has a [homes] section which is commented out.  So using the sys settings I've added my home directory.  The smb.conf is updated to reflect the changes appropriately.  However, if I uncheck the read-only check box setting, it never sticks.  I had to edit the smb.conf manually to set 'read only = no'.  I've tried this in 'administrator mode' as well.

Is this a known problem?  Is there a better KDE utility for managing shares like this?

---

