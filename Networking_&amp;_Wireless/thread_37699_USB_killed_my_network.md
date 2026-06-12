---
title: "USB killed my network"
date: 2005-05-28
forum: Networking &amp; Wireless
---

### Post by Ben Jao Ming on 2005-05-28
Hi all

I'm pretty sure about this since I found a previous example of it on the net. After having connected a USB device my network stopped working after reboot.

**dhclient** returns:

```
sit0: unknow hardware address type 776
```

And then it starts doing alot of unsuccesful DHCPDISCOVER.

I've also done **ifup eth0** :

```
sit0: unknow hardware address type 776

SIOCSIFADDR: No such device

ERROR while getting interface flags: No such device
ERROR while getting interface flags: No such device
sit0: unknow hardware address type 776

```


The other incident I found by googling told me that **chmod +x /etc/init.d/hotplug** would solve my problem but it didn't.


Running **/etc/init.d/hotplug start** returns NOTHING! And running it without paramters doesn't return the usual usage description. So I'm pretty sure that something is corrupt about this file - but all the permissions are set correct  ](*,)

---

### Post by Ben Jao Ming on 2005-05-28
This is btw the other thread that describes kinda what I'm experiencing:

[http://ubuntuforums.org/archive/index.php/t-24954.html](http://ubuntuforums.org/archive/index.php/t-24954.html)

---

