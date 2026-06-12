---
title: "Network Config is not &quot;dancing Samba&quot;"
date: 2005-05-30
forum: Networking &amp; Wireless
---

### Post by Christoph Freitag on 2005-05-30
Hi,

I am trying to access my Win 2K network following [this](http://www.ubuntulinux.org/wiki/SettingUpSamba) guide. However my network config panel does not show the checkboxes (or anything at all) for Windows Networking or WINS Server. There are just the 2 fields for Host Name and Domain Name.

I **can** view and manipulate the shares on my network through Nautilus (Locations -> Network Server).

However I would like to be able to *mount* some of my Windows shares. How do I go about that?

Thanks,
Christoph

Note: As I am using a German localization of Ubuntu my translations of the GUI elements my not be entirely accurate.

---

### Post by fabiand on 2005-05-30
Hello,

try something like:
mount -t smbfs -ouser=foo,password=bar //server/share /mnt/remte_server_directory

else: man mount and look for smbfs

- fabiand

---

