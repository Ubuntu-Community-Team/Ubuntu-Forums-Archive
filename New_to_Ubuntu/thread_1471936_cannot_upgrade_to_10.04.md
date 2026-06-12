---
title: "cannot upgrade to 10.04"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by martyway on 2010-05-03
I'm trying to upgrade from 8.04LTS to 10.04LTS. The update manager does not offer an upgrade. When I try the Alternative CD method I get this.

Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/pool/main/d/dkms/dkms_2.1.1.2-2fakesync1_all.deb Wrong CD-ROM

Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/pool/main/w/wvstreams/libwvstreams4.6-extras_4.6.1-1_i386.deb Wrong CD-ROM

Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/pool/main/w/wvdial/wvdial_1.60.3_i386.deb Wrong CD-ROM

Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/pool/main/w/wvstreams/libuniconf4.6_4.6.1-1_i386.deb Wrong CD-ROM 

Have I downloaded the wrong version?

Marty

---

### Post by Geoff918 on 2010-05-03
Well, the system is looking for a CD in the CD-ROM which it isn't finding. Are you installing from a CD you burned?

Do you have more than one CD drive? Because if so, it *IS* finding a CD, but not the Ubuntu CD.

---

### Post by Geoff918 on 2010-05-03
From the documentation it seems your "preferred" upgrade method is via network.

Please see:

[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

look under the 8.04 LTS to 10.04 LTS heading. :)

---

### Post by Geoff918 on 2010-05-03
Geeze, I finally realized you probably *did* look at that documentation and mounted the CD as prescribed.

However, assuming you're on a multi-cd drive system you may be mounting a different media to cdrom0. Perhaps you might try swapping the media in the bays, or just try cdrom1 instead?

---

### Post by 3rdalbum on 2010-05-04
You need to go to System > Administration > Software Sources and set it to prompt for release updates "Long-Term Service Releases Only". It looks like you might have changed it to read "Never".

---

### Post by martyway on 2010-05-04
I have 1 CD/DVD RW, I have downloaded the Alternate iso twice now from separate sources. I get the same message. I am still confused as to why the update manager does not offer the update.

---

### Post by martyway on 2010-05-04
already checked that. If I set it to Normal releases I get the option to update to 9.04

---

