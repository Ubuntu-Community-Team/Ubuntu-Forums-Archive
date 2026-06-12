---
title: "Ubuntu USB Startup Creator and Debian ISO"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by coldReactive on 2009-08-23
Debian ISO successfully burns to a USB Pendrive, but Debian claims that it's the wrong CD.

Using Debian CD 1 ISO.

---

### Post by loomsen on 2009-08-23
Hello.

I'm using a script I stumbled upon some time and place (slightly changed)

[http://omploader.org/vMjdkNQ](http://omploader.org/vMjdkNQ)

call it with 
sh isotostick.sh /path/to/iso /dev/usb

---

### Post by coldReactive on 2009-08-23
> **loomsen said:**
> Hello.

I'm using a script I stumbled upon some time and place (slightly changed)

[http://omploader.org/vMjdkNQ](http://omploader.org/vMjdkNQ)

call it with 
sh isotostick.sh /path/to/iso /dev/usb

Doesn't do anything, just outputs a help line:

```
ian@ian-desktop:~/Desktop$ sh isotostick.sh /debian-502a-i386-CD-1.iso /dev/sdb
You need to be root to run this script
ian@ian-desktop:~/Desktop$ sudo sh isotostick.sh /debian-502a-i386-CD-1.iso /dev/sdb
[sudo] password for ian: 
isotostick.sh [--reset-mbr] [--noverify] <isopath> <usbstick device>
ian@ian-desktop:~/Desktop$ sudo sh isotostick.sh --reset-mbr /debian-502a-i386-CD-1.iso /dev/sdb
isotostick.sh [--reset-mbr] [--noverify] <isopath> <usbstick device>

```

---

### Post by coldReactive on 2009-08-23
Nevermind, had to remove the / before the ISO.

Also,

```
ian@ian-desktop:~/Desktop$ sudo sh isotostick.sh --reset-mbr debian-502a-i386-CD-1.iso /dev/sdb
Not verifying image...(no checkisomd5 in Ubuntu so skipping)!
unknown or non-unique volume type (--probe-all lists possibly conflicting types)
USB filesystem must be vfat or ext[23]
Cleaning up to exit...
```

even though the target USB is fat16.

---

### Post by loomsen on 2009-08-23
Try calling it with 

sudo sh isotostick.sh debian-502a-i386-CD-1.iso /dev/sdb[color=red]1[/color]

> 
docter[~] /lib/udev/vol_id -t /dev/sdb
unknown or non-unique volume type (--probe-all lists possibly conflicting types)
docter[~] /lib/udev/vol_id -t /dev/sdb1
vfat
docter[~] 


---

### Post by coldReactive on 2009-08-23
> **loomsen said:**
> Try calling it with 

sudo sh isotostick.sh debian-502a-i386-CD-1.iso /dev/sdb[color=red]1[/color]

This error message occurs when I do that:

```
trap: 179: SIGINT: bad trap

```

---

### Post by loomsen on 2009-08-23
Strange.

What if you log in as root instead of running sudo?

> 
[COLOR="Blue"]root[/home/docter/tmp/DISTROS][/COLOR] isotostick.sh foresight-2.1.1-x86_64-dvd1.iso /dev/sdb2
Not verifying image...(no checkisomd5 in Ubuntu so skipping)!
cat: /usr/lib/syslinux/mbr.bin: No such file or directory
Copying live image to USB stick


---

### Post by coldReactive on 2009-08-23
> **loomsen said:**
> Strange.

What if you log in as root instead of running sudo?

Same error, however, after a little while, a new icon comes up on the desktop: **cdtmp.TQSlkQ**, and I can't unmount the USB Drive unless I first unmount this cdtmp (can only unmount as root)

---

### Post by loomsen on 2009-08-23
Well, this is really strange.

You shouldn't get any bad trap messages. That's really weird.
Did you hit Ctrl + C while running the script? I really can't find a reasonable explanation, it works over here. In doubt you can uncomment the trap line after exitclean. (It's a security feature anyways, won't affect the way the script works)

---

### Post by coldReactive on 2009-08-23
> **loomsen said:**
> Well, this is really strange.

You shouldn't get any bad trap messages. That's really weird.
Did you hit Ctrl + C while running the script? I really can't find a reasonable explanation, it works over here. In doubt you can uncomment the trap line after exitclean. (It's a security feature anyways, won't affect the way the script works)

I didn't. I commented it out, then it ran fine however...

When I boot to it, I get nothing but a light gray radial gradient to a dark gray middle, nothing on screen but that radial gradient.

---

