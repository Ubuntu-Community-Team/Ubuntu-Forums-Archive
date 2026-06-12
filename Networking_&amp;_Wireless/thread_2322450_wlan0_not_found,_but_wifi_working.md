---
title: "wlan0 not found, but wifi working"
date: 2016-04-28
forum: Networking &amp; Wireless
---

### Post by richardbures on 2016-04-28
Hello,
 I have a weird problem, when i start ubuntu, pc connect to the wifi as he used to, but I'm not able to reconnect or change wifi connection.


```

ifconfig -a
docker0   Link encap:Ethernet  HWadr 02:42:9d:4c:71:6f  
          inet adr:172.17.0.1  Všesm&#283;r:0.0.0.0  Maska:255.255.0.0
          inet6-adr: fe80::42:9dff:fe4c:716f/64 Rozsah:Linka
          AKTIVOVÁNO VŠESM&#282;ROVÉ_VYSÍLÁNÍ B&#282;ŽÍ MULTICAST  MTU:1500  Metrika:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          kolizí:0 délka odchozí fronty:0 
          P&#345;ijato bajt&#367;: 536 (536.0 B) Odesláno bajt&#367;: 7423 (7.4 KB)


enp2s0    Link encap:Ethernet  HWadr 9c:5c:8e:db:98:da  
          AKTIVOVÁNO VŠESM&#282;ROVÉ_VYSÍLÁNÍ MULTICAST  MTU:1500  Metrika:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          kolizí:0 délka odchozí fronty:1000 
          P&#345;ijato bajt&#367;: 0 (0.0 B) Odesláno bajt&#367;: 0 (0.0 B)


lo        Link encap:Místní smy&#269;ka  
          inet adr:127.0.0.1  Maska:255.0.0.0
          inet6-adr: ::1/128 Rozsah:Po&#269;íta&#269;
          AKTIVOVÁNO SMY&#268;KA B&#282;ŽÍ  MTU:65536  Metrika:1
          RX packets:602 errors:0 dropped:0 overruns:0 frame:0
          TX packets:602 errors:0 dropped:0 overruns:0 carrier:0
          kolizí:0 délka odchozí fronty:1 
          P&#345;ijato bajt&#367;: 53469 (53.4 KB) Odesláno bajt&#367;: 53469 (53.4 KB)


veth48924a2 Link encap:Ethernet  HWadr 22:e5:3f:71:21:04  
          inet6-adr: fe80::20e5:3fff:fe71:2104/64 Rozsah:Linka
          AKTIVOVÁNO VŠESM&#282;ROVÉ_VYSÍLÁNÍ B&#282;ŽÍ MULTICAST  MTU:1500  Metrika:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          kolizí:0 délka odchozí fronty:0 
          P&#345;ijato bajt&#367;: 648 (648.0 B) Odesláno bajt&#367;: 11519 (11.5 KB)


wlp3s0    Link encap:Ethernet  HWadr 80:a5:89:cf:4a:c9  
          inet adr:192.168.1.140  Všesm&#283;r:192.168.1.255  Maska:255.255.255.0
          inet6-adr: fe80::6272:890e:6126:104/64 Rozsah:Linka
          AKTIVOVÁNO VŠESM&#282;ROVÉ_VYSÍLÁNÍ B&#282;ŽÍ MULTICAST  MTU:1500  Metrika:1
          RX packets:8753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7735 errors:0 dropped:0 overruns:0 carrier:0
          kolizí:0 délka odchozí fronty:1000 
          P&#345;ijato bajt&#367;: 7370232 (7.3 MB) Odesláno bajt&#367;: 1566387 (1.5 MB)



```

---

### Post by kek3 on 2016-04-28
Did you try to manually edit the conections?

Terminal: The config file is in /etc/network/interfaces , just edit it with nano or the text editor you prefer!
GUI: in the right up corner, right click on the wifi, edit conections. You can try to add manually wifi conection.

Hope this help!

---

### Post by richardbures on 2016-04-28
GUI:I can edit or add connection this way, but i can't connect to any of them by purpose, only automatically after restart.

interfaces look like something missing, but I do not feel it to mess with it by my own.
```

[COLOR=#000000]$ sudo nano /etc/network/interfaces
[/COLOR]# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

---

### Post by slickymaster on 2016-04-28
*Thread moved to **Networking & Wireless**.*

---

### Post by jeremy31 on 2016-04-28
Your wireless is ```
wlp3s0    Link encap:Ethernet  HWadr 80:a5:89:cf:4a:c9  
          inet adr:192.168.1.140  V&#353;esm&#283;r:192.168.1.255  Maska:255.255.255.0
          inet6-adr: fe80::6272:890e:6126:104/64 Rozsah:Linka
          AKTIVOVÁNO V&#352;ESM&#282;ROVÉ_VYSÍLÁNÍ B&#282;&#381;Í MULTICAST  MTU:1500  Metrika:1
          RX packets:8753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7735 errors:0 dropped:0 overruns:0 carrier:0
          kolizí:0 délka odchozí fronty:1000 
          P&#345;ijato bajt&#367;: 7370232 (7.3 MB) Odesláno bajt&#367;: 1566387 (1.5 MB)
```

As the result of [https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)

---

### Post by richardbures on 2016-04-28
Okey, thanks
and do you know, why i can not connect to wifi, via network setting in top right corner (UNITY) ... it dont search for any wifi

---

### Post by richardbures on 2016-04-28
Im able to connect via:
```

nmcli d wifi connect <WiFiSSID> password <WiFiPassword>

```

---

### Post by jeremy31 on 2016-04-28
Are you using wifi with a hidden SSID?

---

