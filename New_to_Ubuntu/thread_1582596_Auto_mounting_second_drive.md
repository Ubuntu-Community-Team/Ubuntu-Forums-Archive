---
title: "Auto mounting second drive"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by ericstrom on 2010-09-26
Should I be able to see a 2nd IDE drive that I've set up to mount automatically ? I know it's mounted because I checked Disk Utility and it shows up as mounted. Yet when I look at file browser, I don't see anything. Running Lucid Lynx by the way.

I use the following line in fstab to have it mount automatically :
UUID=06eb3868-4edd-4f71-92ca-ad0d871a9a20 /mnt/spare ext4 defaults 0 2

Should I see the drive in the list when I first open the file browser or go to "Places" ?

Maybe it's not supposed to show up the unless I mount it as root instead of a non root ? 

As you can tell, I'm not all that clear with this process or what I'm doing.

---

### Post by coffeecat on 2010-09-26
I'm not 100% sure, but I think that if you mount a partition in /mnt it won't show up in Places. You certainly don't get a desktop icon. You should be able to find it if you open 'Computer' from Places, then Filesystem > mnt > spare.

Try creating a mountpoint in /media and changing your fstab line. That might do it.

**edit:** alternatively, once you've navigated to it with Computer > File System > mnt > spare, create a bookmark from the bookmarks menu in Nautilus and the bookmark will show up in Places.

---

### Post by egalvan on 2010-09-26
> **coffeecat said:**
> I'm not 100% sure, but I think that **if you mount a partition in /mnt it won't show up in Places.**
 You certainly don't get a desktop icon.
 You should be able to find it if you open 'Computer' from Places, then Filesystem > mnt > spare.

Yes, the partition** DOES show** up in "Places" if mounted under /mnt.

No desk-top icon when mounted under /mnt

---

### Post by coffeecat on 2010-09-26
> **egalvan said:**
> Yes, the partition** DOES show** up in "Places" if mounted under /mnt.


Sorry to have to differ, but I've just tried it. A partition mounted to a folder in /mnt does not show up in Places.

---

### Post by ericstrom on 2010-09-26
It's not showing up in Places when mounted in mnt/spare

It is showing up in Places when mounted under /media. But as mentioned in the second reply, it is also showing up on the desktop.

Any ideas on how I get it to show up in Places but not show up on the desktop.

Looks like I'm in the middle at this point

---

### Post by coffeecat on 2010-09-26
> **ericstrom said:**
> Any ideas on how I get it to show up in Places but not show up on the desktop.

Two ways:

Mount in /mnt and add a bookmark as I suggested earlier.

Alt-F2 > gconf-editor > apps > nautilius > desktop > untick volumes_visible. The disadvantage of this is that automouted USB drives don't show icons on the desktop - although you may prefer this.

---

### Post by bsalem on 2010-09-27
It is possible to mount an FS that isn't seen at boot. It used to be that if you wanted an fs mounted at boot that it needed an entry in /etc/fstab.

There ought to be a similar mechanism, something to put an entry from /mnt back into the
boot files, whatever it is called. /etc/mtab contains what is current, what would show up in 'df'. I am not as familiar with how all of this happens in the GUI.

---

