---
title: "Gigaware USB to Ethernet not working -newish to Ubuntu-"
date: 2014-01-22
forum: Networking &amp; Wireless
---

### Post by anonymouscats on 2014-01-22
The ethernet nic on my motherboard stopped working a month or so ago, so I had to pick up a usb to ethernet adapter.
However it doesn't work at all on Ubuntu. I'm also fairly new to linux so please don't get annoyed if I ask how to do most things that I am asked.

```
Bus 009 Device 005: ID 0fe6:9702 Kontron (Industrial Computer Source / ICS Advent)
```

 I also get this mount error when it is first plugged in.

[B]Unable To Mount USB to Ethernet
[/B]```
Error mounting /dev/sr1 at /media/myname/USB to Ethernet: Command-line 'mount -t "iso9660"
-o
"uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500"
"dev/sr1" "/media/myname/USB to Ethernet" exited with non-zero exit status 32: mount: block
device /dev/sr1 is write-protected, mount-read only
mount: /dev/sr1 already mounted or /media/myname/USB to Ethernet busy
```

---

### Post by chili555 on 2014-01-22
If you Google the usb.id 0fe6:9702, you will find but one other thread about this device, also in Ubuntu. In that thread, the device never got working at all. Would you be annoyed If we suggested that you return the device?

[http://ubuntuforums.org/showthread.php?t=2148313](http://ubuntuforums.org/showthread.php?t=2148313)

---

### Post by anonymouscats on 2014-01-22
I have no problem returning it, probably better off just buying a new motherboard in the long run though.

---

### Post by chili555 on 2014-01-22
Is this the typical desktop mobo? PCI and PCIe NICs that work perfectly are pretty cheap; US$12-15 or so.

---

### Post by anonymouscats on 2014-01-22
I will try to order one later and hopefully be able to start using Ubuntu fully and learn more.
Thanks for the help.

---

