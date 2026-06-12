---
title: "issues with copying files TO usbdrive"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by browneyedgirl65 on 2006-09-14
I've got Ubuntu 6.06 with all of the updates as of today.  I've recently started to use a usbdrive (60G hdd in an external casing with USB cable, formatted ext2) for offloading those huge music files after filling up the laptop's hdd. 

OK, so that's the scenario/setup.  First thing I notice is some (pretty good percentage, say 60-80%) of the music files copied to the usbdrive are corrupted -- they act as if they're truncated.

This is what I did, and I have no idea of what is going on (bug, file format, what) or how to resolve it. ](*,) 

Here's what I did. 

On the command line on the hdd, I created a tar.gz file for one of my music directories, using 
tar -cvvf dir.tar dir
and then
gzip dir.tar

I then copied the file over to the usbdrive, which is mounted on /media/musicdrive:
cp dir.tar.gz /media/musicdrive/music_storage

I then cd to that directory but when I gunzip, 
gunzip dir.tar.gz,
I immediately get this message:
invalid compressed data -- format violated

However, back on hdd's music directory, gunzipping that file I'd just copied over works fine.

This happens regardless of whether I use the command line or nautilus to do the above actions.
Also, the file copied over has the same file size but! they have different md5sums.

Help!  I don't know quite what is going on.  I'm entertaining thoughts of reformatting the usbdrive to ext3 instead but I would really like to know what is going on -- bug, old drivers, bad file system to use, what...

Thanks... ](*,)

---

