---
title: "BC43xx card does not appear 8.04"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by DFalconX on 2008-04-28
recently updated my ubuntu, I previously worked very well in 7.10 with ndiswrapper, but disappeared from my newly upgraded configuration of networks:

```
josue@samandrosii:~$ ifconfig
eth56     Link encap:Ethernet  direcciónHW 00:16:d3:ad:a2:5b  
          inet dirección:192.168.1.110  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::216:d3ff:fead:a25b/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:4255 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4165 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:2931353 (2.7 MB)  TX bytes:634669 (619.7 KB)
          Interrupción:220 Dirección base: 0x4000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:1958 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1958 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:99776 (97.4 KB)  TX bytes:99776 (97.4 KB)

josue@samandrosii:~$ lspci | grep Broadcom
04:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

```

---

### Post by grumpylad77 on 2008-04-28
[http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html]("http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html")

Try this link and everythin will work, I have the same card and it works great with this guide.

---

