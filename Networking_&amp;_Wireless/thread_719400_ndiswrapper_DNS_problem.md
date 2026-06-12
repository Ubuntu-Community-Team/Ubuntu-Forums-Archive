---
title: "ndiswrapper DNS problem"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by jii2 on 2008-03-09
Hi,

since i installed gutsy my internet connection is unstable (suddenly dropping when downloading big files). i didn't have this problem with suse 10.3 and windows works smooth.

so i tried replacing the tg3 driver (broadcom ethernet adapter) with ndiswrapper and windows broadcom driver. everything seems to work great except of dns.

ndiswrapper seems to be unable to resolve hostnames eventhough when i switch back to tg3 i have no problems with that.

i use a router with ip 192.168.2.1.

my resolv.conf:

```
#nameserver 192.168.2.1
nameserver 195.34.133.21
nameserver 195.34.133.22
```

(i tried even 192.168.2.1 as my dns which works under windows but caused long delays under suse)

route:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.2.1     0.0.0.0         UG    100    0        0 eth0
```

i can ping my router, i can ping my dns servers and i can ping ip addresses.
but ping [www.google.com](www.google.com) doesn't work.

what am i doing wrong?
thanks.

---

### Post by Phoenixzeus on 2008-03-13
Have you tried disabling IPv6?
In mozilla type "about:config" as the adderss.
Look for network.dns.disableIPv6    - or something similar?
double click on it and restart mozilla.

---

### Post by jii2 on 2008-03-13
hi.

i tried disabling ipv6 for the whole system. however i didn't disable it directly in firefox. but as i said, it's not just the case of firefox. every single application i tried behaves the same.

anyway thanks for the reply.

---

### Post by Phoenixzeus on 2008-03-13
What ISP do you have and do you know if they use proxys?

---

### Post by jii2 on 2008-03-14
my ISP is Chello, u probably don't know it :)
i don't use proxy of my ISP (but don't know if there's some transparent proxy)

anyway, that's one thing i didn't try yet - using proxy. i'll give it a chance and let u know.

---

### Post by ittiam on 2008-03-14
Try this:
```

modprobe -r ndiswrapper
modprobe ndiswrapper

```

Now try connecting to your network.

By the way what are you using to connect to the network? (nm-applet/wifi radar/wpa_supplicant/knetworkmanager...???)

---

### Post by jii2 on 2008-03-15
there's no proxy. that's what i was not sure the other day.

i don't use ndiswrapper for wifi. i use it for wired network (i heared that should work)

restarting the module didn't help. then i even tried restarting the init.d/network script. no success...

---

