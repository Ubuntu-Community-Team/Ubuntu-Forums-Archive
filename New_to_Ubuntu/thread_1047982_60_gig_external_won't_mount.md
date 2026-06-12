---
title: "60 gig external won't mount"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by Jeconti on 2009-01-22
I'm running Intrepid on my Dell Mini 9.

This morning, an external hard drive that I've used before started producing the following error when the drive is connected to the USB port.

Cannot mount volume
mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

I think I understand what it means, but could someone clarify and tell me where I go to fix it?

Thanks

---

### Post by jimmy the saint on 2009-01-22
It sounds like the mountpoint (the folder to which the drive will mount) has some invalid characters.  where are you mounting the drive to?  Oh yeah, and what kind of drive is it? make/model?

---

### Post by Jeconti on 2009-01-23
ahhh, okay, there is some sense to be made now.

The last time I had it in, I was playing to try and get it to mount to home by typing /home into the fields provided by gnome when I right click the drive properties. I passed out before I could finish experimenting and must have screwed it up somehow. So how do I change that now? Is that information buried in a config file somewhere?

The drive is a Hitachi Travelstar, 80gb, 4200 rpm (sigh). It's an old laptop hard drive that I've used as an external for over a year now.

---

### Post by mc4man on 2009-01-23
Read here, same idea, though in your case you only need to edit out the mount_point you used. (in other words you just need to edit the value itself, r.click on the value -> edit and remove the entry, after your done should look like []

[http://ubuntuforums.org/showthread.php?t=1045860](http://ubuntuforums.org/showthread.php?t=1045860)

A quick explanation on changing mount point thru properties

[http://ubuntuforums.org/showthread.php?p=6588072#post6588072](http://ubuntuforums.org/showthread.php?p=6588072#post6588072)

edit: if your unsure post screenshot of gconf-editor (Alt+prnt scrn

---

### Post by Jeconti on 2009-01-23
I read through both the things you posted with no luck. I don't find a listing for drives anywhere in gconf.

Screenshot shot attached.

Yes the drive is attached, yes, it is drawing power from USB, as soon as I plugged it in I got the same error as before.

---

### Post by Jeconti on 2009-01-23
RESOLVED

Dolphin wins the day again!

---

### Post by mc4man on 2009-01-23
Normally if you did change the mount point in the properties of a drive or volume an entry would be created which obviously hasn't occured.

what's your fstab look like?

---

