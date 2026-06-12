---
title: "Ndiswrapper messes up modprobe?"
date: 2008-03-11
forum: Networking &amp; Wireless
---

### Post by ronaldv2li on 2008-03-11
I have HP dv6500 notebook, with broadcom wireless. bcm4312 rev 02 to be exact.

Fwcutter didn't work for me, so I turned to ndiswrapper.
But sth happens when I use ndiswrapper.

I followed this guide: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

And it worked... in a way. My wireless started functioning, but as I rebooted following errors occurred:

1. At startup it said: 
*Loading hardware drivers... 
udevd-event [3845]: run-program: '/sbin/modprobe' abnormal exit
*Starting system clock...
*Loading kernel modules...
*Loading manual drivers...

And thats it, it hangs...

So I pressed ctrl + alt + del ... And it said xserver internal error...
I pressed ctrl + alt + f1 only way I could get gdm start, was by applying:

```
sudo mount -o remount,rw /dev/sda3
sudo gdm
sudo gdm
```

The reason for mounting the drive as rw was because i saw a bunch of read-only filesystem messsages.

2. Login screen came up. Typed in my user and passwd, now it suggested not logging in as there was a problem with home and root, I did log in and again x server error... refusing to initialize GTk+

I have reinstalled Ubuntu several times :S Please help me... everything else is perfect.

Ask for more details :)'

thank you in advance....

Ron

---

### Post by handydan918 on 2008-03-11
Boy, I dunno, but I doubt it was on account of modprobing ndiswrapper. I think you may have another issue there...

---

### Post by ronaldv2li on 2008-03-12
Like what? Can you guess anything? Beacuse these problems occur when I start using ndiswrapper.

---

### Post by handydan918 on 2008-03-12
Simple enough to test...enter rescue mode and do ```
rmmod ndiswrapper
``` then reboot and see if anyone salutes...

:popcorn:

---

### Post by ronaldv2li on 2008-03-12
That command didn't work. It said that ndiswrapper is in use. So I tried to end and kill the process modprobe ndiswrapper through system monitor, but it wouldn't let me.

---

### Post by dmizer on 2008-03-13
post the contents of the following files:

/etc/modprobe.d/blacklist
--and--
/etc/modules

be sure to use the bbcode markups to enclose the contents of the files in [code] format

---

### Post by ronaldv2li on 2008-03-13
/etc/modprobe.d/blacklist: 
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
blacklist bcm43xx
blacklist ssb
blacklist b43
blacklist bcm43xx
```

/etc/modules:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
ndiswrapper
ndiswrapper
```

---

### Post by dmizer on 2008-03-13
edit /etc/modules and remove the second "ndiswrapper"

---

### Post by ronaldv2li on 2008-03-15
I removed the 2nd 'ndiswrapper' but it's still the same :S Any other ideas?

---

### Post by kevdog on 2008-03-15
remove ndiswrapper from the modules file completely and see what happens.

Please list
ndiswrapper -l

---

### Post by ronaldv2li on 2008-03-15
Removed ndiswrapper from the modules file, startup was successful, but I didn't have any wireless.

Running ndiswrapper -l doesn't do a I thing, Just hangs. Btw I can log in only as root.

---

### Post by dmizer on 2008-03-16
if you can't log in with your normal user account, something is seriously wrong with your install.  was this a problem before you followed the guide?

---

### Post by ronaldv2li on 2008-03-18
No problems, before using the guide. :S i wouldn't say there is anything wrong with the install, I used the original CD requested from canonical.
I also tried using Wifi-radar and wicd, but these didn't work.
Any other ideas?

---

### Post by ronaldv2li on 2008-03-22
C'mon can anyone help me?

---

