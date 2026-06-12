---
title: "path to usb?"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by owners4life5 on 2010-07-22
how can i access my pendrive through the terminal?

any help is greatly appreciated.
thanks

---

### Post by cariboo on 2010-07-22
dmesg will tell you the device label, once you know the device label, it just a matter of telling it where to mount. You can create a directory in /media:

```
sudo mkdir /media/thumb
```

Then mount the device:

```
sudo mount /dev/sdX /media/thumb
```

---

### Post by staf0048 on 2010-07-23
Try this:

```
cd /media
```

then "ls" to list available devices.  The USB drive should be in there somewhere.  I just stuck mine in and it's referred to as F169-EF04.  I don't know how it got that name...

Then just cd to the drive.

---

### Post by owners4life5 on 2010-07-23
i created the directory... when i mount it though, i get this:

```
root@brian-laptop:~# sudo mount /dev/sdX /media/thumb
mount: special device /dev/sdX does not exist
```

---

### Post by staf0048 on 2010-07-23
**AH!!!**  Why are you running as root????

The "X" in sdX is a place holder.  For example, my hard drive is known as "sda" so your usb drive might be known as "sdb" "sdc" etc.  But the drive should mount automatically, so you shouldn't need to worry about that.

To find out what your drive is listed as go to:

```
cd /dev
```

and type ls.  There will be lots of stuff in there, but look for something similar to the above examples.

---

### Post by Paqman on 2010-07-23
As staf0048, it will already be mounted somewhere in /media, so just browse to that folder and have a look.

---

### Post by owners4life5 on 2010-07-23
> **staf0048 said:**
> **AH!!!**  Why are you running as root????

a new update.. it screwed up everything and now it says that its running in low graphics mode... and nothing is working... check this out

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1506463&page=1](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1506463&page=1)

what a mess.....

i.l also mark this as solved... thanks to both of you

---

