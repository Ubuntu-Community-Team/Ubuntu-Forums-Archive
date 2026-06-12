---
title: "Dual booting- Adding XP on top of karmic"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by mrmagoo1077 on 2010-04-21
I gave up windows completely (had vista) for Ubuntu 9.10 when it was first released, and it has been great (also first real ubuntu experience.  Now my class requires me to use Autodesk inventor so I have to run Windows.

I want to install windows in a new partition while keeping my Karmic.  I would be creating the partitions with partition magic.  I do not want to uninstall my ubuntu- spent alot of time making it how I want it to be.  Ive searched around alot- but everything was for Pre-karmic and doesn't use grub2.  Any help would be appreciated.

---

### Post by Mark Phelps on 2010-04-21
Any MS Windows install will overwrite the MBR, so you will have to reinstall GRUB2 when you're done, but I would first download and burn a GParted LiveCD (which you can get from distrowatch.com), boot from that, and use that to shrink your Ubuntu partition to make room.

Then, I would download a burn a Clonezilla LiveCD (get that from the same place), boot from that, and image off your Ubuntu partition(s) to an external drive or USB stick.

After that, you can boot from the XP CD and install it with no worries about losing your Ubuntu stuff because you'll have the means to quickly restore it if needed.

---

