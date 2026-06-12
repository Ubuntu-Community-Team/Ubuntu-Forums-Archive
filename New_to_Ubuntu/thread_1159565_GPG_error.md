---
title: "GPG error:"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by shadowlands on 2009-05-14
GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch cdrom:[Ubuntu-Server 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu-Server 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by michy99 on 2009-05-14
Go to System->Administration->Software Sources. Click the Third Party Software tab. Make sure the lines which start with cdrom are unchecked.

---

### Post by shadowlands on 2009-05-14
thanks
> **michy99 said:**
> Go to System->Administration->Software Sources. Click the Third Party Software tab. Make sure the lines which start with cdrom are unchecked.

---

