---
title: "vga notworking"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by latiff on 2010-01-27
aim using ubuntu 9.10 asus k8v-mx all drivers are working but vga is
not working the driver is VIA Technologies, Inc. K8M800/K8N800/K8N800A
[S3 UniChrome Pro] (rev 01)

iam the driver in mother board cd in tar file i don't how install in
symteic manager the driver installed is X.Org X server -- VIA display
driver

Open Chrome is a project for the development of free and open-source drivers
for the VIA UniChrome video chipsets.

Originally called the 'snapshot' release, since it was a snapshot of an
experimental branch of the unichrome cvs code, this is a continued development
of the open source unichrome driver (from [http://unichrome.sf.net](http://unichrome.sf.net)) which
also incorporates support for the unichrome-pro chipsets.

Support for hardware acceleration (XvMC) for all chipsets has subsequently
been ripped out of the unichrome.sf.net driver. Therefore your only option if
you wish to make use of the acceleration features of your VIA chip with free
and open-source drivers is to use this version of the driver.

Canonical provides critical updates for xserver-xorg-video-openchrome
until April 2011.

---

### Post by LuisGMarine on 2010-01-27
By default Ubuntu should provide some drivers for it.  Can you please post the output of this command?

```
sudo lshw -C video
```

This will allow more people to know the exact make/model of you video card to further help you.  Through this help thread I will be referring to this [guide]("https://help.ubuntu.com/community/BinaryDriverHowto").  Please feel free to go about trying the steps mentioned in the guide, and if you have any questions please post back.

---

### Post by latiff on 2010-01-27
*-display UNCLAIMED     
       description: VGA compatible controller
       product: K8M800/K8N800/K8N800A [S3 UniChrome Pro]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 bus_master cap_list
       configuration: latency=64 mingnt=2
       resources: memory:f4000000-f7ffffff(prefetchable) memory:fb000000-fbffffff memory:faf00000-faf0ffff(prefetchable)

tell step step method slove this problem

---

### Post by latiff on 2010-01-27
tell step step method slove this problem

---

