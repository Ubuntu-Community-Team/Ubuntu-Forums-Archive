---
title: "Intrepid: Complete freeze when mounting cifs share"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by bring on 2008-11-04
Since upgrading from 8.04 to 8.10, i get a complete system freeze (flashing keyboard leds, etc) when trying to mount a cifs/smb share. I have used the following command without any problems in 8.04 and before:

```
mount -t cifs //nas1.home/websites /mnt/www -o uid=bring,gid=bring,workgroup=HOME,username=bring
```

In 8.10 the share appears to get mounted, but then 1 or 2 seconds later, the system freezes completely, i have not been able to find any entries in the usual log files.

Is anyone else experiencing this?

---

