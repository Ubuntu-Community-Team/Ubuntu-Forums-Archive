---
title: "Changing disks in my RAID array"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by mgbridges on 2011-07-01
Hi,

I have a small home server running 8.04 Hardy Heron. I'm not an Ubuntu expert but with the help of these forums I managed to get it up and running 2 or 3 years ago. And I've basically not needed to do anything to it since.

Anyway, I have a RAID1 (mirrored) array built from 2 x 200GB drives. It's starting to fill up so I've bought a pair of 1TB drives. I'm trying to figure out how I go about transferring the data across to the new drives - is it as simple as taking one of the 200GB drives out of the array, adding in one of the 1TB drives, letting the mirror rebuild itself then doing the same with the other drive?

Cheers,

Martin

---

### Post by psusi on 2011-07-01
In theory you could do that, followed of course, by expanding the array to make use of the larger drive, but instead I would suggest building the new system around the new disks, installing 10.04 in the process, and the manually copying your data over from the old disk.  Or you can copy the system to the new disks, remove the old disks, then upgrade to 10.04.  This way you start with a fresh clean filesystem with the latest features and no fragmentation.

---

### Post by mgbridges on 2011-07-01
Thanks. The problem with going to 10.04 is that I don't think it supports my old motherboard with its onboard ATI Radeon X1250 graphics chipset. Hence why I'm sticking with an old version.

---

### Post by psusi on 2011-07-03
> **mgbridges said:**
> Thanks. The problem with going to 10.04 is that I don't think it supports my old motherboard with its onboard ATI Radeon X1250 graphics chipset. Hence why I'm sticking with an old version.

Why would you think that?

ATI has apparently dropped support for some of their older video cards in their proprietary driver, but the open source driver has not.

---

### Post by mgbridges on 2011-07-03
I ran the upgrade process recently and before it got too far into it it said my graphics chipset was not supported, so I aborted the installation.

---

### Post by psusi on 2011-07-03
Are you using the proprietary driver?  If so you may need to switch pack to the open source one.

---

