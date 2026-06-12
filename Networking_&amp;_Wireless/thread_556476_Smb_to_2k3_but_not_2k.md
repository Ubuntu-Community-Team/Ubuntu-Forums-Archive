---
title: "Smb to 2k3 but not 2k"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by elspiko on 2007-09-21
First off, I have searched the forums and haven't found an answer, but if there is a post with this issue, I apologise.

Right, I've been trawling multiple forums for ages with no joy.

The issue is I can connect to shares on Windows 2003 Servers no problem (both at the terminal and with fstab). I can't however connect to 2000 shares via command line or fstab,  but I can via "Connect to Server".

I've tried mounting using cifs and smbfs, using various different parameters within fstab.

When I try and mount i get

```
mount error 13 = Permission denied
```

Edited the permissions on the shares from the Win Server. I'm really at my wits end!!

I don't really want to connect it to AD if possible, but if there is no other option, if you could suggest a decent HOWTO, then I'd be very greatful :).

---

