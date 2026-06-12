---
title: "Wi-Fi and LAN devices doesn't access to internet"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by csegurav on 2011-01-19
Hello friends!

in my house I have a couple of "net points" that allows me to access to internet (where I connect the ethernet cable). In pcs, there are 2 S.O. (Xubuntu 10.10 and Windows XP sp3). 

There is also an Access Point ( Linksys DualBand WAP55AG) connected to one of the "net points" and allows me to connect to internet Wi_Fi.

I bought a WI-Fi adapter "D-Link DWA-525 Wireless N 150 Desktop Adapter". 

The trouble is that in Xubuntu, even when I have access to the local network (i.e. I can make a ping to other host in the same network)I haven't access to the internet, and this issue is expanded to the LAN connection, so I haven`t any internet connection only I can send pings to my neighbours.

This issue is even stranger, this happens in Xubuntu when it starts, and sometimes can connect to internet, but when I disconect the interface (WiFi or LAN) and connect it again, it doesn`t connects

I hope somebody could help me!!

Thanks!

Chris

---

### Post by cariboo on 2011-01-19
Can you ping google by number?

```
ping 72.14.213.147
```

---

### Post by csegurav on 2011-01-24
Sorry for not responding duroing the last few days!!. 

No, there isnt any answer. Only there is an answer if I make a ping to another host in the same local network.

---

### Post by sadaruwan12 on 2011-01-24
Through your Wi-Fi you was able to use the inter net before this crisis. if so just remove your Wi-Fi and switch it for time being connect your ubuntu computer the LAN and see whether it works or not if does post back so we can help you.

---

### Post by The Cog on 2011-01-24
The output from these three commands would help diagnose the problem:
```
ifconfig
route -n
cat /etc/resolv.conf
```Also, do you know if you use a proxy server when accessing the web? I don't know where that setting is stored in Linux, but it may be significant.

---

