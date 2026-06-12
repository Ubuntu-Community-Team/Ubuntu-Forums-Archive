---
title: "Ubuntu 9.10 Doesn't recognize my CD-Rom"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by JesusSavez on 2009-10-30
When I try to burn a file it doesn't recognize my CD-Rom.

---

### Post by philinux on 2009-10-30
Open a terminal and use this. Post back the results.

```
sudo lshw -c disk
```

---

### Post by archkidd on 2010-04-22
I don't see a reply to your latest post, but I have just installed 9.10 on a Vaio laptop and while the CD Rom shows in Nautilus its properties say 'unknown' and the 'permissions could not be determined' and it will not open (manual button under screen) nor does VLC seem to recognize that it is there.  Running lshw as you suggest gives this:
 *-cdrom
       description: DVD writer
       product: UJ-832D
       vendor: MATSHITA
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw

What should I be doing?  Thanks

---

