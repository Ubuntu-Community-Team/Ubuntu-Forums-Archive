---
title: "Enable Network Write Access"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by chalewa on 2007-11-30
i have a simple network setup to share files between my desktop and laptop (wirelessly)...

i can read files on the laptop from the desktop fine, but i cannot write to the desktop. I have read and write access enabled through gnome on the desktop, but i still don't have permission on the laptop. any ideas?

---

### Post by victorbrca on 2007-12-01
Are you using Samba? How did you set up ur share on smb.conf?

If you want, run this code. It will post the last 30 lines on your smb.conf file and remove uncoments.

```
tail -n 30 /etc/samba/smb.conf | grep -v '^#' | grep -v '^;'
```


Vic.

---

