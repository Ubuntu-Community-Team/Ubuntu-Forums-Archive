---
title: "Wireless broken (Cannot obtain IP Address)"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by bullyballa on 2008-04-24
After upgrading to 8.04 my wireless broke.  I'm using ndiswrapper and can see all the networks in my area yet I cannot connect. I tried using Wicd instead of Network Manager, yet no luck.  It times out on "Obtaining IP"

Any ideas?

Thanks in advance,
A.J.

---

### Post by bullyballa on 2008-04-25
I think I found the problem I ran dmesg in terminal and it said this
```
[  144.518664] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  144.519671] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  239.746480] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  239.889330] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

Though I have no idea how to fix that... any help would be appreciated

---

### Post by schmildo on 2008-04-25
Give some more details about your wireless settings; Are you using WPA?

I had the same problem, (not obtaining an IP address) until I picked a Key index. I was using WPA2 Personal authentication with AES encryption.
  When I edited the properties of my wireless connection on my laptop to use key 1, it worked. and of course...

**. /etc/init.d/networking restart**

... can never be overused.

---

### Post by portach king on 2008-04-25
I'm having the ame trouble with the b43 driver. Won't connect unless I'm very close by the router.
Won't conect to the wireless network in college at all.

---

### Post by portach king on 2008-04-25
I'm having the same trouble with the b43 driver. Won't connect unless I'm very close by the router.
Won't connect to the wireless network in college at all, which is unsecured.

---

### Post by bullyballa on 2008-04-25
> **schmildo said:**
> Give some more details about your wireless settings; Are you using WPA?

I had the same problem, (not obtaining an IP address) until I picked a Key index. I was using WPA2 Personal authentication with AES encryption.
  When I edited the properties of my wireless connection on my laptop to use key 1, it worked. and of course...

**. /etc/init.d/networking restart**

... can never be overused.

Yeah the problem seems to be because I was trying to use WPA.  I can connect if it unsecured, but not if I try and use WPA. I don't quite know why though.  I thought I was setting the key correctly in Wicd.  Any ideas on how I can try and get it working with encryption?

---

