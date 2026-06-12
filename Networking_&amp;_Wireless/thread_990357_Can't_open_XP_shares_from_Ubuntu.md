---
title: "Can't open XP shares from Ubuntu"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by so_savar on 2008-11-22
Hi.

Needless to say I'm a newbie to Ubuntu. I have manegd to setup Samba so I can access the Ubuntu shares from my XP network clients, but I'm not able to open the XP shares from Ubuntu. The XP PCs are visible from the Ubuntu network file system but not the shared folders. I have turned on all access options in XP.

Tennis anyone?

Regards,
SO

---

### Post by Iowan on 2008-11-24
> **superprash2003 said:**
> try typing smb://x.x.x.x where x.x.x.x is the ip of the windows machine.. it hopefully should open the shared folders.. [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)

Sometimes someone else says it better - and deserve the credit...

---

### Post by so_savar on 2008-11-24
Thank you Iowan!

Now I know that I can connect and that the shares will mount and open properly. But, is there a more generic approach, i.e. is it possible to connect without typing the ip adress explicitly? As I have quite a number of PCs connected via DHCP, the ip will change from time to time. Of course I can make them static, but I see this as a last resort. I guess what I´m looking for is some sort of name resolving mechanism that works from Ubuntu to XP.

br,
SO

---

### Post by Iowan on 2008-11-24
Winbind might make an invisible Ubuntu box show up, but probably won't make the Windows machines show up (but I *could* be wrong).  The DNS server needs to know about hostnames of leased addresses.  **dnsmasq** will supposedly do that, but I haven't given it close investigation... yet!

---

