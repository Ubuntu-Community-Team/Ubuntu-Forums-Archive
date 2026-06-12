---
title: "How to Install Broadcom??"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by geomarsh on 2010-08-06
I went to system>admin>package and tried to install the broadcom.  It said it ran.  When I went to select the drivers there was nothing found.  What's the trick?  I tried going to a term window and tried (install pkg 'bcmwl-modaliases') but that's didn't help even with sudo apt-get ......

Anyone??

---

### Post by snowpine on 2010-08-06
Hi Geomarsh, here's the Ubuntu documentation on Broadcom cards:

[https://wiki.ubuntu.com/WifiDocs/Driver/Broadcom43xx](https://wiki.ubuntu.com/WifiDocs/Driver/Broadcom43xx)

Don't skip the first step! This tells you exactly which card you have so you can proceed accordingly. Post the results here if you want help. :)

```
lspci -vvnn | grep 14e4
```

(In case you are new to terminal commands, go to Applications, Accessories, Terminal, and always cut & paste to eliminate the risk of typing mistakes.)

---

### Post by Bachstelze on 2010-08-06
The restricted drivers manager should be all you need.

---

### Post by snowpine on 2010-08-06
> **Bachstelze said:**
> The restricted drivers manager should be all you need.

Wouldn't that be nice. :)

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/511379](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/511379)

---

