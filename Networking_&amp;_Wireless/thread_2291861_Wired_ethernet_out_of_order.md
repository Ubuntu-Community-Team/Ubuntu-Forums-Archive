---
title: "Wired ethernet out of order"
date: 2015-08-23
forum: Networking &amp; Wireless
---

### Post by Antonio_Feijoo on 2015-08-23
[COLOR=#000000]I installed Ubuntu 14.04 LTS as a dual boot on windows vista ultimate.  Ethernet Wired connections doesn't seem to be working. Also, eth0 does[/COLOR][COLOR=#000000] show up on ifconfig -a. But without Add. inet  neither mask, etc. When apply dhcp manually i got this: 

[/COLOR]eth0:avahi Link encap:Ethernet  direcciónHW 00:24:1d:13:3d:08  
          Direc. inet:169.254.2.180  Difus.:169.254.255.255  Másc:255.255.0.0
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
[COLOR=#000000]
Any help on getting the wired connection sorted? 

Thanks a lot[/COLOR]:guitar:

---

### Post by praseodym on 2015-08-23
Please run the wireless script from the sticky thread and show the outputs (its also for LAN)

---

### Post by Antonio_Feijoo on 2015-09-02
Sorry, I don´t know much about Ubuntu, only a few commands.
If you tell me how ? I really appreciate all your help.:guitar:

antonio@antonio-EG31M-S2:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:24:1d:13:3d:08 
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)
 
eth0:avahi Link encap:Ethernet  direcciónHW 00:24:1d:13:3d:08 
          Direc. inet:169.254.2.180  Difus.:169.254.255.255  Másc:255.255.0.0
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
 
lo        Link encap:Bucle local 
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:65536  Métrica:1
          Paquetes RX:437 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:437 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0
          Bytes RX:33935 (33.9 KB)  TX bytes:33935 (33.9 KB)

---

### Post by praseodym on 2015-09-04
Please show the outputs of
```

lspci -nnk
lsmod
route -n
cat /etc/resolv.conf
```
Can you connect temporarily via wireless?

---

