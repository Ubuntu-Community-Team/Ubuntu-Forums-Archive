---
title: "Usb stick as ramdrive?"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by Twizzle on 2009-04-15
I have 8.04 sever edition installed on my home server. One of the programs I am using is Zoneminder which now has an option to use a ramdisk or tmpfs partition.

My setup is three drives - two as software RAID and the third holding /var.

I was going to try and repartition the drive with /var on it, making /var smaller and having a tmpfs partition (if I have understood what i need right!)

I then realised that I have a spare 2GB USB flash stick and wonder if I can leave that plugged into the server all the time and have it as a ramdisk.

I have searched Google but everything seems to be about Booting from the USB drive which I don't want.

Does any one know if this is possible and if so - any pointers?

Thanks

---

### Post by Hospadar on 2009-04-15
I don't see why you couldn't mount /var to the usb stick.  You'd just have to edit /etc/fstab accordingly (which I suggest you read tutorials and look in the community docs in my sig if you don't know how to do that)

Your current /etc/fstab should however give you a basic gist of how it will look.

Basically, format your usb stick ext3 and set /etc/fstab to mount it's uuid to /var

Am I understanding what you want to do?  I'm not totally sure what you need, could you give a link to whatever instructions you're looking at that are prompting this re-format?

That said, are you sure you want to use a usb stick as /var?  That get's written to a lot and flash memory has a (relatively small compared to disks) finite number of writes and using it in a high write area like /var could burn it out quickly.  I assume a tempfs type partition would be used for intermediate data (i.e. lots of writes) as well.

I think you might be better off re-formatting or just picking up another small drive (a 2GB hdd would be practically free nowadays)

---

### Post by Twizzle on 2009-04-15
Thanks for the quick reply. I'm not sure if I explained myself properly though. I want to keep /var on the existing drive and just wanted to have the temp ramdrive partition on the stick. The only thing written to it would be temp files from zoneminder which I guess would be a lot really. I guess I will give it a go and see how I get on.

---

### Post by kpatz on 2009-04-15
The idea behind a ramdisk (tmpfs) is fast access to temporary files that are stored in RAM (not on a disk at all, except maybe the swap partition).

A USB drive will be slower than just keeping the zoneminder temp files in whatever directory in /var that they're being put in now.

To use a ramdisk, you would mount a tmpfs to the directory where zoneminder puts its temporary files.  For example, let's say that's /var/tmp.  The command:

**sudo mount -t tmpfs -o rw,noexec,nosuid,nodev,mode=1777 vartmp /var/tmp**

will do the trick.  Since it's dynamically created in RAM, you don't need to have a partition or hard drive available to mount a tmpfs.

Note that tmpfs defaults to half the size of RAM for its maximum size.  So, if you have 1GB of RAM, tmpfs will default to a 512 MB maximum size (it won't use all this RAM initially unless you fill it with data).  You can override this by adding the size= option on the mount.

Also, any data stored in a tmpfs will be lost when unmounted or when you reboot.

---

### Post by Twizzle on 2009-04-15
Thankyou, that does make perfect sense and I was obviously getting confused about it all! Linux has a great learning curve!!

I will give it all a try. Thanks again.

---

### Post by theozzlives on 2009-04-15
It would be incredibly slow.

---

