---
title: "Airsnort in Hardy?"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by altonbr on 2008-06-06
What happened to airsnort in Hardy?

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=airsnort](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=airsnort)

---

### Post by altonbr on 2008-06-06
I guess it was orphaned?

[https://launchpad.net/ubuntu/+source/airsnort](https://launchpad.net/ubuntu/+source/airsnort)


> 
0.2.7e-3
Superseded in hardy-release on 2007-10-18
Published in gutsy-release on 2007-06-19

airsnort (0.2.7e-3) unstable; urgency=low

  * Orphaning this package

 -- Ubuntu Archive Auto-Sync <email address hidden>   Tue,  19 Jun 2007 16:00:19 +0100



How can I install it on my Ubuntu machine now?

---

### Post by altonbr on 2008-06-06
I guess using the Gutsy binary works: [http://packages.ubuntu.com/gutsy/i386/airsnort/download](http://packages.ubuntu.com/gutsy/i386/airsnort/download)

Can a mod close this please?

---

### Post by altonbr on 2008-06-30
Except, airsnort (the Gusty package) fails to work in Hardy:
> sh: /sbin/wlanctl-ng eth1 lnxreq_wlansniff enable=true channel=3 keepwepflags=false prismheader=false > /dev/null
sh: /sbin/wlanctl-ng: not found

---

### Post by marlboro05 on 2008-08-07
I am trying to install it on hardy too.
I guess we ll need to do it the real way and configure, make, make install it.

---

### Post by chronos00 on 2008-08-12
I was hoping to use airsnort in ubuntu hardy...

Anyone knows why isn't this package available?

---

### Post by damonjablons on 2008-08-23
[http://www.getdeb.net/app/AirSnort](http://www.getdeb.net/app/AirSnort)

This link seems to work.  I just installed it from here, and it's working fine.

Once you download the ".deb" file, make sure you give it permissions to execute:

(if you download it to your desktop)
```
$ chmod 777 ~/Desktop/airsnort_*
```

Then you can double click on it and install it.

:guitar:

---

