---
title: "live cd will not load ubuntu"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by moondoggy17 on 2009-01-09
i'm trying to install ubuntu 8.04.1 LTS but when the disk starts and i chose to install or use the live cd the boot screen shows up but stops a little ways in

my system specs
intel celeron D 2.93ghz
1.24gb of ram
nvidia geforce 6200 OC
80gb hard drive
20gb hard drive

---

### Post by Malalo on 2009-01-09
Check the CD for errors (there's an option for this when the menu appears)

If the CD checks ok, then try downloading the Alternate CD for non-graphic installation

---

### Post by ThePinkPoo on 2009-01-09
Also if a new cd is needed, burn at a little slower speed than max.

---

### Post by Bölvaður on 2009-01-09
> **ThePinkPoo said:**
> Also if a new cd is needed, burn at a little slower speed than max.

like x4 or at max x8 , perhaps some one has good experience with more speeds?

---

### Post by moondoggy17 on 2009-01-09
alright i burned a alternet image at 4x speed reboot then check disk, install reboot, and now it will not start like last time but i do see this

Init: rc-default main process (4254)terminated with status 139

---

### Post by Bölvaður on 2009-01-09
this is all very strange, lets find where it fails.

download failure:
if you have the .iso files laying around still, try to install them on virtiual machine to see if those are ok, and check the checksum of md5 or what ever it is called.

burn failure:
already done...

ram... hey check the ram for defects, you can do it off the live cd.

my best guess would be those two. but as a noob my guess should be considered as it is.. a guess from a fool ;)

---

### Post by supererki on 2009-01-09
write custom installer with 2.6.27 kernel. 
i know this issue .. im not quite sure, but it has something to do with 2.6.24 kernel not recognising SATA disks... or what so ever. it is fixed in 2.6.27. another way to skip this error is by turning on AHCI (advanced host controller interface) in your BIOS.

---

### Post by moondoggy17 on 2009-01-09
ram checks fine 
could not find ahci in bios
and how would i make a custom installer

---

### Post by moondoggy17 on 2009-01-09
could my video card be the problem i have heard that are some compatibility issues with some video cards

---

