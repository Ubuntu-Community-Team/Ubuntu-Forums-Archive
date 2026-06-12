---
title: "Unable to obtain IP adrees in wired connection"
date: 2015-11-05
forum: Networking &amp; Wireless
---

### Post by Nilanjan_Sircar on 2015-11-05
Hi,I am using Ubuntu 14.04 LTS on my Lenevo G40-80 laptop. I am able to connect to wireless, but unable to connect to wired connection in my University. The wired connection was working so far when I was setting the configuration manually. But recently my university has changed policy that the configuration has to be obtained automatically every time I connect by automatic DHCP. After that I am unable to connect to university LAN! I searched a lot in internet past few days, but I could not resolve this issue. It will be very helpful if someone can help. Thanks in advance.


These are few information if it helps.

```

$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback



```

```

$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 68:f7:28:9e:75:f7  
          inet6 addr: fe80::6af7:28ff:fe9e:75f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:144436 errors:0 dropped:17 overruns:0 frame:0
          TX packets:1513 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18175884 (18.1 MB)  TX bytes:612581 (612.5 KB)




```
Please let me know if more information is needed.

---

### Post by SeijiSensei on 2015-11-05
If the policy changed, it may be that they now require more authentication than before like a certificate.  You need to ask the school's IT department for help.

---

### Post by Nilanjan_Sircar on 2015-11-08
Thanks for your reply. But that is not the case. Other people using ubuntu can connect with their own laptop. I talked with the system administration and they said that my Mac ID is correctly registered with a static IP. So it seems something is screwed up in the ubuntu in my machine.

---

