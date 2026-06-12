---
title: "Help: Network with 3 pcs. Only 2 work at the same time."
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by Yuzem on 2008-09-14
**Setup**
pc1:
+eth0   -->   pc0
+eth1   -->   modem
+eth2   -->   pc2

**Problem**
pc0 works perfectly from pc1, I can ping to it.
pc2 doesn't work, I can't ping pc2 but if I do:
```
sudo ifconfig eth0 down
```
Then I can ping pc2 with no problems.

**More info**
ifconifg in pc1:
```
eth0      Link encap:Ethernet  direcciónHW 00:00:6c:b6:65:e3  
          inet dirección:192.168.0.1  Difusión:192.168.0.255  Máscara:255.255.255.0
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:10061 (9.8 KB)  TX bytes:13390 (13.0 KB)
          Interrupción:220 Dirección base: 0xa000 

eth1      Link encap:Ethernet  direcciónHW 00:16:b5:e4:7d:38  
          inet dirección:???.???.???.???  Difusión:255.255.255.255  Máscara:255.255.252.0
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:138846 errors:105 dropped:0 overruns:0 frame:105
          TX packets:98184 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:116801159 (111.3 MB)  TX bytes:53258478 (50.7 MB)

eth2      Link encap:Ethernet  direcciónHW 00:06:4f:5d:6e:79  
          inet dirección:192.168.0.3  Difusión:192.168.0.255  Máscara:255.255.255.0
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:616 errors:0 dropped:0 overruns:0 frame:0
          TX packets:204 errors:0 dropped:0 overruns:0 carrier:24
          colisiones:0 txqueuelen:1000 
          RX bytes:60269 (58.8 KB)  TX bytes:29988 (29.2 KB)
          Interrupción:16 Dirección base: 0xec00 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:455 errors:0 dropped:0 overruns:0 frame:0
          TX packets:455 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:36836 (35.9 KB)  TX bytes:36836 (35.9 KB)

```

pc0 (eth0 in pc1) has:
ip: 192.168.0.2
subnet mask: 255.255.255.0
Gateway: 192.168.0.1

pc2 (eth2 in pc1) has:
ip: 192.168.0.4
subnet mask: 255.255.255.0
Gateway: 192.168.0.3

route -n (in pc1):
```
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
???.???.???.?   0.0.0.0         255.255.252.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         200.115.240.1   0.0.0.0         UG    0      0        0 eth1
```

---

### Post by Iowan on 2008-09-15
More than one NIC in the same subnet generally confuses a machine. If you're doing connection sharing, [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") may help.

---

### Post by Yuzem on 2008-09-15
In first place I only want to do networking with the 3 pcs.
I have a script that shares the connection with pc0 but even if I disable that the problem persist.

How to setup a network with 3 pcs?
Isn't that a simple setup?

---

### Post by Iowan on 2008-09-15
Check [this]("http://ubuntuforums.org/showthread.php?t=902436") thread.

---

### Post by Yuzem on 2008-09-22
Ok, I have been reading about this and I think that I need to make ubuntu act as a router using the command "route" but I don't know how to do that.
I couldn't find any info.
Any ideas on how to do it with my setup?

---

