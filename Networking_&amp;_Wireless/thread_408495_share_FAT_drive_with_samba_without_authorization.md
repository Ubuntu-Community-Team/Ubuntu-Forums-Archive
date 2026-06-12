---
title: "share FAT drive with samba without authorization"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by mc^2 on 2007-04-13
Hi, I'm trying to configure my home network (Ubuntu+a couple of WinXPs) to share directories with no authorization. I followed the guide which says smth like:
```

[public]
  comment = Public Folder
  path = /home/public
  public = yes
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup

```
However, I'm not able to share my FAT hard drive (/media/fat/smth) this way, probably because I'm not able to manage the access rights correctly (I think mounted drives have smth like 770 mask).

Any ideas on how to make it work?

---

### Post by Protoss on 2007-04-18
Try putting "guest ok = yes" in there, it seems to be the magic key to getting my Samba shares working just like XP.

---

