---
title: "mac hard drive mounted on ubuntu read only?"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by DJpattiecake on 2010-06-22
please help, my neighbors imac went kaput and im trying to back up their data for them. After taking apart the beast i put the hard drive in a thermaltake dock connected to my ubuntu laptop via esata (it can do usb also)

now the hard drive is mounted automatically and i can surf around the files, but when i try to copy from it, it says i dont have permission to do so. I ran nautilus as root and tried to take ownership of the drive, but it told me the drive is read only. What do I do?

btw I dont know alot of kernal commands for mounting and permissions so include any commands with tips :)

---

### Post by Bachstelze on 2010-06-22
Ubuntu, and Linux in general, cannot write to HFS+ filesystems used by most Macs. You shouldn't need to write to the disk to backup its contents, though...

---

### Post by DJpattiecake on 2010-06-22
thats exactly what I thought (im not cutting, im copying), but this is what I get:

[[IMG]http://img205.imageshack.us/img205/9652/screenshotst.th.png[/IMG]](http://img205.imageshack.us/i/screenshotst.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by DJpattiecake on 2010-06-22
I got it, I had to su root, then cp in terminal manually, then when the transfer is complete to my local drive I can take ownership with my user account, thanks

---

