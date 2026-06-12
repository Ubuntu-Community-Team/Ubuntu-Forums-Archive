---
title: "eth0 is not working"
date: 2014-12-18
forum: Networking &amp; Wireless
---

### Post by cucuru2 on 2014-12-18
hello. I'm not able to configure eth0. 

This is what I have:

```

rocio@rocio-laptop:~$ nano /etc/network/interfaces

auto lo
iface lo inet loopback
 
auto eth0
iface eth0 inet dhcp



```

```


rocio@rocio-laptop:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:23:ae:24:a9:8b  
          Direc. inet:192.168.0.101  Difus.:192.168.0.255  Másc:255.255.255.0
          Dirección inet6: fe80::223:aeff:fe24:a98b/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:86 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:474 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000
          Bytes RX:8340 (8.3 KB)  TX bytes:58331 (58.3 KB)
          Interrupción:18
 
lo        Link encap:Bucle local 
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:233 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:233 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0
          Bytes RX:18465 (18.4 KB)  TX bytes:18465 (18.4 KB)


```


```

rocio@rocio-laptop:~$ route
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0



```

I tried:

```

rocio@rocio-laptop:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
^C
--- 192.168.0.1 ping statistics ---
9 packets transmitted, 0 received, 100% packet loss, time 8063ms


```

so as this didn't work I tried:
```

rocio@rocio-laptop:~$ sudo ifdown eth0
rocio@rocio-laptop:~$ sudo ifup eth0
ssh stop/waiting
ssh start/running, process 3696
rocio@rocio-laptop:~$


```

But it still doesn't work.

What can I do?

Thank you in advance

---

### Post by grahammechanical on 2014-12-18
This is what my /etc/network/interfaces file says

> # interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


Do you notice the difference? Network Manager in Ubuntu does not use the interfaces file and if we have anything in addition to what I have quoted then Network Manager will not work.

Regards.

---

