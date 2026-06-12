---
title: "ubuntu 8.10 and ethernet"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by binary_dreamer on 2008-11-07
hi. i have installed ubuntu 8.10 in a dual boot laptop. everything works perfect apart from the internet. i cannot get connected to the internet. if take a look at the attachment u can see that the network manager can see that i get an ip. although the ifconfig nothing. 
the thing is that i tried to connect to a different router and everything went smoothly. i have to mention that in my router i connect perfectly many other computers and the same laptop while booting in windows. any ideas?

---

### Post by cariboo on 2008-11-07
There are a couple of things you can try in a terminal type:

```
sudo dhclient eth0
```

This may get you a working ip address

Also are you sure you are using the correct driver for your network card, according to the info screen your nic has a marvel chip set. Could you paste the output of:

```
sudo lshw -C network
```

in your next post.

Jim

---

### Post by binary_dreamer on 2008-11-08
i got an issue over here. the laptop works perfect when i connect it to another router. the problem exists at my place.
here is the post.

---

### Post by HereInOz on 2008-11-08
Try setting a static IP address and setting your DNS servers to those specified by your ISP.  If that gives you an internet connection, then it is probable that the router is a D-Link, or some models of Netcomm, which do not pass DNS on correctly.

I had that problem and I used it to justify heaving the D-Link out the window and getting a decent modem/router.

---

### Post by binary_dreamer on 2008-11-09
hi could u point me how to set the static ip from gui, please?

---

### Post by binary_dreamer on 2008-11-09
check the attachment. what am i doing wrong? the ip now is static.

---

