---
title: "dvd drive won't stay open"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by bwallum on 2009-10-12
I have a sata dvd drive, a Samsung Writemaster, that works well with one exception. When I eject a cd the door opens but then closes immediately. 

The device is listed as:
*-cdrom
       description: DVD-RAM writer
       product: CDDVDW SH-S223B
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: SB01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted

The medium was a Karmic live cd and I installed from it without any problem. If I stop the system before the os boots up then the button on the drive works as expected and the door stays open appropriately.

How can I configure the device so that when it opens it stays open, until I manually push it in or press the device open/close button?

---

### Post by swoody on 2009-10-13
This seems to be a known bug at the moment. Try running:
```
sudo killall mtd
```
To kill the mtd process, and try it again. There is also another thread in the forums with a bit more info on this issue:
[http://ubuntuforums.org/showthread.php?t=1275886](http://ubuntuforums.org/showthread.php?t=1275886)

If this doesn't take care of your issue, please let us know, and we can look further into your specific problem :)

---

### Post by bwallum on 2009-10-21
> If this doesn't take care of your issue, please let us know, and we can look further into your specific problem :)

That didn't work unfortunately. I remember a Samsung drive doing the same thing some time ago, then it started working ok. That same drive is working fine on an upgraded AMD64 karmic. 

The subject drive is a similar 'Writemaster' Samsung drive on a new build AMD64 running karmic but from a new beta install. I guess at this stage of a release I should just wait a while.

---

### Post by sandyd on 2009-10-21
> **bwallum said:**
> I have a sata dvd drive, a Samsung Writemaster, that works well with one exception. When I eject a cd the door opens but then closes immediately. 

The device is listed as:
*-cdrom
       description: DVD-RAM writer
       product: CDDVDW SH-S223B
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: SB01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted

The medium was a Karmic live cd and I installed from it without any problem. If I stop the system before the os boots up then the button on the drive works as expected and the door stays open appropriately.

How can I configure the device so that when it opens it stays open, until I manually push it in or press the device open/close button?
try poking the hole in the cd drive to open it next time.

---

### Post by bwallum on 2009-10-26
> **carlee said:**
> try poking the hole in the cd drive to open it next time.

...no change I'm afraid. The interesting thing is the drive opens and closes as normal if the OS isn't booted. As soon as Karmic is loaded the tray will not stay open.

---

