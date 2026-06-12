---
title: "Sharing an NTFS Partition on Feisty with Windows XP"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by Roblobob on 2007-08-30
I have two computers on my home network, one dual-booting both Feisty and Windows XP and the other with Feisty alone (with NTFS partitions from a previous XP install).

What I'd like to do is share the NTFS partitions on the Feisty box with Feisty and Windows XP on the dual-booting box over the network.

The NTFS partitions on the Feisty box are set to mount on boot and I can view the files with ease on that box. Although I can make the drives visible over the network (SMB) when I try to access them I get an error telling me that the directory can not be read. Using NFS I can't even see the drives over the network.

Does anyone have any ideas?

Thank you,

---

### Post by Zorael on 2007-09-01
One solution, though not very "secure", would be to open your /etc/samba/samba.conf (or whatever its name is. may be smb.conf), scroll down to the definitions of your shares, and make sure the line:
```
guest ok = yes
```
...is included in each. I like to make sure 'browsable = yes' is included, too.

There's also some way to add guest accounts somehow to make sure that only the accounts logged in on the Feisty/XP box could access them (meaning, if someone else managed to get into your network they still couldn't access the shares), but I don't know how. Google might prove helpful.

---

### Post by Zorael on 2007-09-01
Okay, now that I'm home I see that the file is indeed /etc/samba/smb.conf.

And for comparison, I offer you an exerpt of my share definitions:
```
[video]
path = /media/main/video
writable = no
read only = yes
guest ok = yes
browseable = yes

[audio]
path = /media/main/audio
writable = no
read only = yes
guest ok = yes
browseable = yes

[share]
path = /media/main/share
writable = yes
guest ok = yes
browseable = yes
```

(and no, I don't know which of 'writeable' and 'read only' is the one to use, eheh.)

---

