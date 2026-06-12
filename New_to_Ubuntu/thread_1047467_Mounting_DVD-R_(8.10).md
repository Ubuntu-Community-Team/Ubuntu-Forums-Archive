---
title: "Mounting DVD-R (8.10)"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by WileyGaia on 2009-01-22
When I insert a CD-R things are all good - it mounts and recognizes it fine, but when I insert a DVD-R I get an error "Cannot mount volume - Unable to mount UDF volume" and then "DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."
I have an LG dvd writer
Any ideas?

---

### Post by taurus on 2009-01-22
Is it a blank DVD or does it have stuff on it?

---

### Post by WileyGaia on 2009-01-22
Its got stuff (photos) on it

---

### Post by WileyGaia on 2009-01-22
I actually have never tried inserting a blank dvd-r - its all new to me... thanks

---

### Post by bsharp on 2009-01-22
Are you sure you are inserting it into a drive that can read DVDs?

DVD and CD are not compatible with each other; to read a dvd you must have a dvd drive.

Most computers built within the last 2 years or so usually have a combination drive, i.e. they can read both.

---

### Post by WileyGaia on 2009-01-22
Its a combo drive... i am scratching around right now to try find the user manual for the exact spec...

---

### Post by taurus on 2009-01-22
How did you burn those photos to a DVD?  Did you copy them in windows, mac, or even Linux?

---

### Post by WileyGaia on 2009-01-22
hi - the photos were copied to the dvd-r in windows. I cant find the drive's manual but i did find the software cd that came with it, its called "LG DVD Writer Solution"

---

### Post by taurus on 2009-01-22
It could be how you burnt it in windows.  Do you have another DVD that you can insert into the drive and see if Ubuntu automounts it?

---

### Post by WileyGaia on 2009-01-22
ja! you're right, just tried another dvd (just a regular movie) and it mounted fine... sure, its asking for a search of the suitable "codec" but it mounted all right. but now how do i get our holiday pics off this unmountable dvd and onto my machine? do i need to burn in a specific way in windows...?

---

### Post by mc4man on 2009-01-22
> do i need to burn in a specific way in windows...

If your using vista, when you put the blank dvd and choose to burn a data dvd with windows you'll get a small pop up, "Prepare this blank disc"
Click on the "show formatting options"
Choose 'mastered'

8.10 can't read 'live system' formatted disks, even though it's up to udf 2.5 capable.
(with a patched kernel module 8.04 can read all disks 

If your using Xp find another burning app (xp uses udf 1.02 which is fully compatible.

The other option is to install Imgburn in wine, use in read mode to rip to an iso and choose iso9660/udf 1.02 as format to rip to.(Imgburn supports all udf formats up to 2.6

---

### Post by WileyGaia on 2009-01-23
thanks people... i will try using a different burning app in XP

---

