---
title: "Mount UDF DVD iso-file across NFS"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by cvacubo on 2006-11-04
Hello.

Maybe you can help me. I have Kubuntu Edgy.

How I can mount UDF dvd iso-file across NFS ?

I created iso file (dd if=/dev/scd0 of=/qqq.iso). But My DVD is UDF dvd disc.
And the I can mount iso file, for example: sudo mount -o loop /qqq.iso /mnt/iso1.

But when I want mount /mnt/iso1 accross NFS (sudo mount localhost:/mnt/iso1 /mnt/iso2) I have error: mount: localhost:/mnt/aix failed, reason given by server: Permission denied

My /etc/exports file is:

/mnt/iso1        *(async,insecure,all_squash)
/mnt/iso2        *(async,insecure,all_squash)

How I can solve this problem ?

P.S. When I mount ISO9660 iso-file I have not this problem, everything is OK with ISO9660 iso-files.

Thanks a lot.

---

### Post by hotdoog on 2007-12-21
This is the same problem I have, any solutions?

---

### Post by stuporglue on 2008-01-27
Just another "Me too".

---

### Post by aboutblank on 2008-01-31
Me too. :-(

---

