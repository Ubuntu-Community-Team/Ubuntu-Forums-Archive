---
title: "Problems with network connection"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by JuanNZ on 2011-02-05
Hi everybody!

Happy to be part of this community!

I have a problem with the network connection of my computer. I have a Compaq Presario C700 with Ubuntu 9.10 (Karmic Koala) installed. Recently, I was assigned a new office in my workplace and I was told I would be able to connect to the network just by plugging in the network cable. The wireless connection was working fine before that.

So I did and nothing happened. As a result, I used the command 
> pppoeconf to try to configure the cable network but what I got in return is that now my computer cannot detect any wireless connection neither the cable connection.

I used the following commands and this is the information I got:


> ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:1b:38:e7:85:44  
          Dirección inet6: fe80::21b:38ff:fee7:8544/64 Alcance:Enlace 
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1 
          Paquetes RX:3 errores:0 perdidos:0 overruns:0 frame:0 
          Paquetes TX:8 errores:0 perdidos:0 overruns:0 carrier:0 
          colisiones:0 long.colaTX:1000 
          Bytes RX:252 (252.0 B)  TX bytes:588 (588.0 B) 
          Interrupción:16 Dirección base: 0x1000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0 
          Dirección inet6: ::1/128 Alcance:Anfitrión 
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1 
          Paquetes RX:4 errores:0 perdidos:0 overruns:0 frame:0 
          Paquetes TX:4 errores:0 perdidos:0 overruns:0 carrier:0 
          colisiones:0 long.colaTX:0 
          Bytes RX:240 (240.0 B)  TX bytes:240 (240.0 B) 

wlan0     Link encap:Ethernet  direcciónHW 00:1e:4c:9a:00:0d  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1 
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0 
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0 
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B) 

wmaster0  Link encap:UNSPEC  direcciónHW 00-1E-4C-9A-00-0D-00-00-00-00-00-00-00-00-00-00  
          ACTIVO FUNCIONANDO  MTU:0  Métrica:1 
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0 
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0 
          colisiones:0 long.colaTX:1000 
          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B) 

Route
Tabla de rutas IP del núcleo 
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz

/etc/resolv.conf. 
bash: /etc/resolv.conf.: No existe el fichero ó directorio

hostname
juanf-laptop 

cat /etc/network/interfaces 

auto lo 
iface lo inet loopback 


auto dsl-provider 
iface dsl-provider inet ppp 
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf 
provider dsl-provider 

auto eth0 
iface eth0 inet manual 

Does anybody have an idea of what the problem is related to and how can it be fixed. My apologies because the set up of my OS is in Spanish.

Thanks in advance for the help

Cheers, 

Juan

---

### Post by cwsnyder on 2011-02-05
I think your problem was using pppoeconf instead of NetworkManager to configure your network interface.  You aren't connecting to a DSL modem, you are connecting through a router to the Internet.  In your /etc/network/interfaces file edit using vi or nano and remove the lines:```
auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider 
```Retry and see if your eth0 interface connects properly.

---

### Post by JuanNZ on 2011-02-06
Thanks for your reply cwsnyder!
 
I did what you suggested, using nano I deleted the lines you specified. I rebooted the computer to see if now it could detect any network, but it still does not even detect the wireless connections.
 
Now the file looks like this:
 
```
 
cat /etc/network/interfaces
auto lo
iface lo inet loopback
 
auto eth0
iface eth0 inet manual

```
 
Any ideas?
 
Cheers

Hello again.
 
After I followed instructions from cwsnyder I runned the following:
[FONT=Batang][SIZE=3][/SIZE][/FONT] 
```
 
ifconfig 

lo        Link encap:Bucle local  

          Direc. inet:127.0.0.1  Másc:255.0.0.0

          Dirección inet6: ::1/128 Alcance:Anfitrión

          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1

          Paquetes RX:4 errores:0 perdidos:0 overruns:0 frame:0

          Paquetes TX:4 errores:0 perdidos:0 overruns:0 carrier:0

          colisiones:0 long.colaTX:0 

          Bytes RX:240 (240.0 B)  TX bytes:240 (240.0 B)

 
 
wlan0     Link encap:Ethernet  direcciónHW 00:1e:4c:9a:00:0d  

          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1

          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0

          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0

          colisiones:0 long.colaTX:1000 

          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

 
 
wmaster0  Link encap:UNSPEC  direcciónHW 00-1E-4C-9A-00-0D-00-00-00-00-00-00-00-00-00-00  

          ACTIVO FUNCIONANDO  MTU:0  Métrica:1

          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0

          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0

          colisiones:0 long.colaTX:1000 

          Bytes RX:0 (0.0 B)  TX bytes:0 (0.0 B)

 
 
lshw -C network

  *-network               

       description: Wireless interface

       product: AR5001 Wireless Network Adapter

       vendor: Atheros Communications Inc.

       physical id: 0

       bus info: pci@0000:01:00.0

       logical name: wmaster0

       version: 01

       serial: 00:1e:4c:9a:00:0d

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless

       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg

       resources: irq:16 memory:91300000-9130ffff

  *-network DISABLED

       description: Ethernet interface

       product: RTL-8139/8139C/8139C+

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 1

       bus info: pci@0000:02:01.0

       logical name: eth0

       version: 10

       serial: 00:1b:38:e7:85:44

       size: 100MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s

       resources: irq:16 ioport:1000(size=256) memory:91200000-912000ff

```
 
And that is what I got. Hope it helps
 
Cheers,
 
J

---

### Post by cwsnyder on 2011-02-06
Have you tried sudo networkmanager or sudo wicd to see if they can find your network interface?

---

### Post by JuanNZ on 2011-02-07
Hi cwsnyder,

I finally solved my problem! 

I was in a bit of an awkward situation. Apparently the reception of the wireless network in the place where I am working is very poor, so my laptop was not able to detect any signal unless I move closer to the hotspot. ):P However, I imagine the changes you first suggested did had a positive effect, because before that the laptop could not detect any wireless network even if I stand below the router. 

Following your suggestions, I installed Wicd network manager and de-installed the default network manager that comes with Ubuntu 9.10. It took a long time and lots of up-dates to get it done. Here is the code:

                     ```
juanf@juanf-laptop:~$ sudo apt-get install wicd


```Finally,  I rebooted my computer and tried to connect using the cable. Wicd instantly recognised the wired network, and here I am, happily replying from my laptop which is sitting on my desk! :p  

At first glance, I reckon Wicd network manager is far more simple than the default Network Manager. However, I might be mistaken given I am not using the latest version of Ubuntu, which hopefully has some improvements in terms of the default network manager.

Thank you very much from your patience and help. I learnt heaps!

Juan

---

