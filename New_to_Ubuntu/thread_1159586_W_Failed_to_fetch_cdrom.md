---
title: "W: Failed to fetch cdrom:"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by shadowlands on 2009-05-14
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu-Server 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu-Server 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by caffienefree on 2009-05-14
You need to add the GPG key for Medibuntu. See [https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories).

If you're using the cd-rom for packages instead of the online repositories, issue _sudo apt-cdrom add_.

---

### Post by Joeb454 on 2009-05-14
As well as that, you're also set to be using the Ubuntu CD as a software source.

Go to System &#8594; Administration &#8594; Software sources to change the sources & make sure CD is **not** checked :)

---

### Post by shadowlands on 2009-05-14
Thanks for your help

---

