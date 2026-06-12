---
title: "Samba Error Detection"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by jpc82 on 2008-03-08
Does samba provide any error detection at all?  I was wondering since i think i have a bad cable and want to know if samba will handle the issue, and if so if it logs the error detection issues.

---

### Post by mrsteveman1 on 2008-03-08
If you have a bad ethernet cable, the CRC on the ethernet frames should fail the check and the endpoints should retransmit the frames. SMB also uses TCP which has its own integrity checks, so if those fail it would also retransmit failed packets.

If neither of those things ever happen the cable isn't bad enough to cause data corruption, but it could still slow things down with interference.


I'm not sure samba does any sort of checking itself anyway, what problem are you having?

You can check for bad frames on the ethernet NIC by using ethtool:

```
sudo ethtool -S eth0
```

---

