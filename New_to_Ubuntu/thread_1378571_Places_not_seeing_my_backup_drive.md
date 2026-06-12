---
title: "Places not seeing my backup drive"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by jermza on 2010-01-11
Just noticed this now, but when I click on Places, it usually shows my second HD (called 'Backup').  For some reason, it's not showing it now.

However, when I click on Computer, I can see it as one of the thumbnails.

Any idea what's happening, and how I can fix this?  Should I reboot or something?

---

### Post by J V on 2010-01-11
admin > hard drives (check if its hidden)

---

### Post by jermza on 2010-01-11
Oh dear...

A few days ago, I broke Ubuntu.  So I followed some advice from these forums and successfully re-installed Ubuntu.  But, looking at the attached screenshot, I think I might have installed Ubuntu onto my backup drive, instead of the primary drive (with Windows).

I'm not a techie, so I don't know what's going on now.  :(

Ideas?

---

### Post by corncob on 2010-01-11
> **jermza said:**
> Oh dear...

A few days ago, I broke Ubuntu.  So I followed some advice from these forums and successfully re-installed Ubuntu.  But, looking at the attached screenshot, I think I might have installed Ubuntu onto my backup drive, instead of the primary drive (with Windows).

I'm not a techie, so I don't know what's going on now.  :(

Ideas?

Looks to me like Windows is on the primary partition, Ubuntu on the extended partition and your backup drive has been formatted by windows. Maybe that has something to do with it not showing up in Places.  Try installing ntfsprogs from the Synaptic Package Manager and see if that helps.

---

### Post by J V on 2010-01-11
there should be a button at the top of the devices window called "Mount partition"

Click the backup drive then click mount partition

As for it not showing up in places, I have the same quirk with my recovery partition...

Its probably possible to add it manually through gconf-tool, but I don't know how...

---

