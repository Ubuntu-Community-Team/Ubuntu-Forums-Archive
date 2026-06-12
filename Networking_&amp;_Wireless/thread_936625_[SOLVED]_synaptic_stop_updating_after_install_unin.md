---
title: "[SOLVED] synaptic stop updating after install uninstall anonproxy"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by hecato on 2008-10-03
HI there, at my school tehre is a proxy that dont let me use IRC, so I searched in synaptic for a proxy and I found anonproxy, I installed it via synaptic configured proxy of FF to point to localhost:4001 and runn it via /etc/init.d/anonproxy start IIRC.

After see that it continue without  letting me use IRC (via chatzilla I supose use the same config as FF) and also the pages would not show up, I deleted completely with config files anonproxy.

My actual problem, is that synaptic has stoped working, because apparently it try to connect to (or via) localhost:4001 even that anonproxy is already uninstalled .




This is a part of the log show in synaptic after hit refresh packages button.


```

W: Imposible obtener http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  No pude conectarme a localhost:4001 (127.0.0.1). - connect (111 Conexión rechazada)

W: Imposible obtener http://mx.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  No pude conectarme a localhost:4001 (127.0.0.1). - connect (111 Conexión rechazada)

.......

W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-es.bz2  No pude conectarme a localhost:4001 (127.0.0.1). - connect (111 Conexión rechazada)

W: Imposible obtener http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-es.bz2  No pude conectarme a localhost:4001 (127.0.0.1). - connect (111 Conexión rechazada)

W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.


```

this is my ifconfig

```

ifconfig 
eth0      Link encap:Ethernet  direcciónHW 00:1d:09:be:95:c8  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:17 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:2418 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2418 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:120900 (118.0 KB)  TX bytes:120900 (118.0 KB)

wlan0     Link encap:Ethernet  direcciónHW 00:1e:4c:32:c2:c0  
          inet dirección:192.168.1.102  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::21e:4cff:fe32:c2c0/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:22596 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19676 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:20227084 (19.2 MB)  TX bytes:3286968 (3.1 MB)
          Interrupción:17 Memoria:f9ffc000-fa000000 


```If youo need to know other thing, let me know.


By the way, Im writing from FF in my Ubuntu... if that is of any info.

---

### Post by hecato on 2008-10-03
Turning out that I also need to uninstall tor package apart from anonproxy.

---

