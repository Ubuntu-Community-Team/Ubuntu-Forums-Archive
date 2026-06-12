---
title: "AR5007eg / ndiswrapper - 'link is not ready'"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by xaitax on 2008-04-27
Hi,

I have a problem with my wireless lan in Ubuntu x86_64 - Hardy Heron.

Since madwifi is not supporting my chipset in x86_64 at the moment, I have to use ndiswrapper with Windows XP drivers. After successfully installing everything dmesg shows the following output:
```
[   31.426792] ndiswrapper: using IRQ 16
[   31.485397] NET: Registered protocol family 17
[   31.625786] wlan0: ethernet device 00:1e:4c:88:70:c3 using serialized NDIS driver: net5211, version: 0x50003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
[   31.630331] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

```

Finally the chipset was recognized. After I ran into problems while connecting. I have only a WEP-crypted net for testing now.

I tried to edit the *interfaces* by hand and after I tried the connection with wicd. Nothing works at all. :/

The only thing I find is the following output in /var/log/messages:
```
Apr 27 15:11:32 w00t kernel: [  503.756024] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

Did anyone of you also had this problem?

Regards,
Alex

---

