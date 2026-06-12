---
title: "[SOLVED] NetBios names in Uuntu"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by drtyoman on 2008-05-23
I am running a monitor program, on a Win XP box. It cannot get netbios name from my Ubuntu box. I have updated the smb, nsswitch and dhcp3 config files and installed winbind, as suggested here in other posts, but no luck. What am I missing?

---

### Post by jrusso2 on 2008-05-23
Are you running the samba server as well as the samba client?

There is a place to put the name in the /etc/samba.conf

---

### Post by drtyoman on 2008-05-23
No, but samba server should not be necessary for name resolution. I did add group & host names to the smb.conf file. I have it working now! It turns out that the host line in nsswitch.cong is sensitive to where you insert "WINS". I had it at the end of the line; when I moved it to second place, after "files" it worked. (This was indicated in other post responses; I had not previously tried it. :(

---

