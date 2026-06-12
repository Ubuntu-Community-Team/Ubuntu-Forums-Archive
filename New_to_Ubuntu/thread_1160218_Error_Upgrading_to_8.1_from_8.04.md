---
title: "Error Upgrading to 8.1 from 8.04"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by Nutopia on 2009-05-15
Howdy,

I'm trying to upgrade to Ubuntu 9.04. I'm currently on Ubuntu 8.04. I understand I need to first upgrade to 8.1. When trying to upgrade to 8.1 I receive the following error messages:

> W:Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download, they have been ignored, or old ones used instead.

I'm not sure what to do now. Can someone help me?

Thanks!

---

### Post by Nutopia on 2009-05-15
I'm sorry. I just realized this was a common error and a duplicate post. I found my answer via search. I guess I'm not all that unique.

---

### Post by Nutopia on 2009-05-15
In case anyone hits this thread, here is what fixed my problem:

> this looks like you need to edit the file /etc/apt/sources.list
Code:

gksu gedit /etc/apt/sources.list

Add a # symbol at the beginning of the first line where it starts ...deb cdrom...


---

