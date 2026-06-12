---
title: "Network manager not detecting wireless"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by homy06 on 2006-10-27
I upgraded from dapper to edgy stable and I no longer have wireless detected in the network manager.

I downloaded the new ndiswrapper and network manager from automatix2 and was able to get the driver installed, but for some reason network manager doesn't list the wireless option for networks. 

I have a smc usb wireless adapter and I used ndiswrapper to get it installed in dapper, worked great, but no longer, eeeeeerrrrwwwwittt


here's some info

```
  
 *-usb:1 UNCLAIMED
                      description: Generic USB device
                      product: USB 802.11b WLAN DEVICE
                      vendor: Intersil Americas
                      physical id: 2
                      bus info: usb@1:2.2
                      version: 1.32
                      serial: 1
                      capabilities: usb-1.10
                      configuration: maxpower=500mA speed=12.0MB/s

```

---

### Post by homy06 on 2006-10-27
i would really appreciate the help here...please



here is what ndiswrapper -l gives me

```

ndiswrapper -l
Installed ndis drivers:
smcwusb32       driver present, hardware present 


```

---

### Post by homy06 on 2006-10-31
Bump

---

### Post by saxsux on 2006-10-31
I'm having a similar problem in Dapper.
Network Manager detects my wired network, not my wireless card that I installed with ndiswrapper.

A solution would be appreciated :-)

---

### Post by -Chi.0 on 2006-10-31
Check this link for help w/ NdisWrapper on Edgy](*,) 
[http://ubuntuforums.org/showthread.php?p=1692550#post1692550]("http://ubuntuforums.org/showthread.php?p=1692550#post1692550")
I hope this helps:-k

---

