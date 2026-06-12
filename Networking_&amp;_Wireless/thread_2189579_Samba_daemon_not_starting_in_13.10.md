---
title: "Samba daemon not starting in 13.10"
date: 2013-11-23
forum: Networking &amp; Wireless
---

### Post by sputnikuk on 2013-11-23
Hi all.

I'm trying to run samba.  When i run  "service samba start" i get no error messages.  when i run /etc/init.d/samba status i get the following messages:
```

 * nmbd is not running
 * smbd is not running
[/ CODE]

I have tried running "/etc/init.d/samba start", again, no error messages,  I have also tried reinstalling the package. "dpkg -l samba" gives the following output:
[CODE]
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                          Version             Architecture        Description
+++-=============================-===================-===================-================================================================
ii  samba                         2:3.6.18-1ubuntu3   amd64               SMB/CIFS file, print, and login server for Unix

```

Any ideas people?

Thanks,
       Rob.

---

### Post by Morbius1 on 2013-11-23
That's interesting. I don't know if that's a remnant from the Debian source ( where there actually is a "samba" service ) that Ubuntu forgot to remove or if this is a new feature that doesn't quite work yet but there has been no "samba" service in Ubuntu for quite some time. It's been separated into into it's component daemons and it's controlled in /etc/init not /etc/init.d.

Anywho, try starting it this way:
```
sudo service smbd start
sudo service nmbd start
```

---

### Post by sputnikuk on 2013-11-23
Sorted, thanks.

---

