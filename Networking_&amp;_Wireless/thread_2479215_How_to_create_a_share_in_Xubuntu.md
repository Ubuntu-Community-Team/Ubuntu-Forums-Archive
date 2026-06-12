---
title: "How to create a share in Xubuntu?"
date: 2022-09-18
forum: Networking &amp; Wireless
---

### Post by peyre on 2022-09-18
I recently had to reinstall Xubuntu (22.04) from scratch on my main desktop.  Everything's working fine, except I'm not sure how to create a share.  On my previous setup I installed samba and created the shares in Samba from inside Settings Manager.  However that doesn't seem to be a thing any more.  I want to create two shares, one of my home folder and one of my data drive mounted in ~/Storage, so I can access my data from my laptop or my family's Windows boxes.  No need for any special security or anything; I just want to be able to access the data.

---

### Post by mikewhatever on 2022-09-18
You install samba, and then define shares in /etc/samba/smb.conf. Use "smbpasswd -a" to add users as needed.

---

### Post by #&amp;thj^% on 2022-09-18
It's says 20.04 but a check, I'm sure it will work with 22.04 as well: [https://linuxconfig.org/how-to-configure-samba-server-share-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-configure-samba-server-share-on-ubuntu-20-04-focal-fossa-linux)

---

### Post by peyre on 2022-09-18
Thanks!  The instructions there worked.  The bit with [FONT=Courier New]sudo smbpasswd -a linuxconfig[/FONT] failed for some reason, but I was able to access both my new shares from a Windows box once I added the following after doing the other things the page said to:

[FONT=Courier New][homedir]
  comment = public anonymous access
  path = /home/leon/
  browsable =yes
  create mask = 0660
  directory mask = 0771
  writable = yes
  guest ok = yes
[storage]
  comment = public anonymous access
  path = /home/leon/Storage/
  browsable =yes
  create mask = 0660
  directory mask = 0771
  writable = yes
  guest ok = yes[/FONT]

---

### Post by #&amp;thj^% on 2022-09-18
> **peyre said:**
> Thanks!  The instructions there worked.  The bit with [FONT=Courier New]sudo smbpasswd -a linuxconfig[/FONT] failed for some reason, but I was able to access both my new shares from a Windows box once I added the following after doing the other things the page said to:

Yes it would fail that was the example name they were using "linuxconfig" you would use that command with one of your users instead.
IE:```
sudo smbpasswd -a leon
``` would add the user "leon". ;)

---

### Post by peyre on 2022-09-18
Oh yeah, of course.  Missed that bit.  Done.

---

