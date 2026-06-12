---
title: "Home network setup and shared folders"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by r1ch on 2008-11-08
Hi everyone, 
I am trying to search for information on setting up a home network between 1 Ubuntu and 1 Windows machine via a wireless router which will allow me to view shared folders on each machine, perform automated backups etc, and am having little luck finding relevant information and wording my searches correctly.

Does anyone know of a tutorial, post or other source of information that will guide me through the steps to do this please?

Thanks

---

### Post by jmidgley on 2008-11-08
Not a single Howto, no but:

Do your windows and ubuntu machines have IP addresses? Can they see each other (with ping)?

Samba on the ubuntu side, syncback on the PC side is the route I took.

Samba is a bit gruesome, but Webmin makes it easier to get going.

HTH a tiny bit, at least.

John

---

### Post by r1ch on 2008-11-08
I'll take a look at samba and syncback then.

Thanks for the pointer.

---

### Post by Iowan on 2008-11-08
[Samba]("https://help.ubuntu.com/community/SettingUpSamba")
[Peer-peer]("http://ubuntuforums.org/showthread.php?t=202605")

---

