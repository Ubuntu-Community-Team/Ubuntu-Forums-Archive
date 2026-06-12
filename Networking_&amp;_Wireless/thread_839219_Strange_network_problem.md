---
title: "Strange network problem"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by phasel on 2008-06-24
Hi,

I have a problem that I can't solve. We have a small network with about 10 pc's. All are windows XP except for two. The server just installed, which is ubuntu server 8.04 fully updated. It is a dell poweredge 840, and has many services running correctly, dns, dhcp, apache, mysql, samba...
The other non windows is my laptop, ubuntu-desktop 8.04 hardy.

All other pc's see the server in the network, can ping, get the samba shares... except for me. The server correctly gives me the ip address through dhcp, but initially, I cannot see it. ping does not work, I cannot ssh, I can't get dns results... I only get it through arp command. It is the only evidence that it is actually there in the network.
And then, sometimes, it just answers, I can connect and do everything, but if I do not connect to it for some time, same problem again. So far, the only thing I have found out that works (so long), is opening a screen with a ping to the server and leave it there open.

BTW, if server pings to me, then I see it immediately.
This is frustrating, and I do not know what to do. I have checked logs, and I cannot find any evidence that I can suspect as an error. And then my laptop works fine with every other machine I have ever encounter, so I am really lost. I do not know where the error might be. Server, my laptop... no idea, both work fine with the windows xp machines.

Thanks a lot for your help,

  Best regards,

      phasel

---

### Post by SpaceTeddy on 2008-06-24
do you have any firewalling software installed (firestarter of an equivilant ?). Also, what is your network configuration when this does NOT work. 

Can you please supply the output of the following commands:

```
ifconfig
route -n
cat /etc/resolv.con
iptables -L -vnx
```

hope we can figure this out :)

---

### Post by phasel on 2008-06-24
Hi,

Thanks a lot for your fast response. As far as I know, no firewalls.
From my laptop:

ifconfig:
```
eth0      Link encap:Ethernet  direcciónHW 00:18:8b:b8:d8:49  
          inet dirección:192.168.1.45  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::218:8bff:feb8:d849/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:33810 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26443 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:36372572 (34.6 MB)  TX bytes:6369479 (6.0 MB)
          Interrupción:18 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:8518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8518 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:1078241 (1.0 MB)  TX bytes:1078241 (1.0 MB)

wlan0     Link encap:Ethernet  direcciónHW 00:19:d2:8f:7f:ee  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:378929 errors:0 dropped:0 overruns:0 frame:0
          TX packets:373772 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:333811811 (318.3 MB)  TX bytes:136068585 (129.7 MB)

wmaster0  Link encap:UNSPEC  direcciónHW 00-19-D2-8F-7F-EE-00-00-00-00-00-00-00-00-00-00  
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

route -n

```
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

cat /etc/resolv.conf

```
search atsamadrid.lan
nameserver 192.168.1.2
nameserver 80.58.0.33

```

sudo iptables -L -vnx (I had to do it with sudo)

```
Chain INPUT (policy ACCEPT 450132 packets, 364872294 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 450382 packets, 151227996 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

```

And from the server:

ifconfig

eth0      Link encap:Ethernet  direcciónHW 00:19:b9:fe:dd:7e  
          inet dirección:192.168.1.2  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::219:b9ff:fefe:dd7e/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:199482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:454165 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:144758292 (138.0 MB)  TX bytes:107318712 (102.3 MB)
          Interrupción:16 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:13037 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13037 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:4559864 (4.3 MB)  TX bytes:4559864 (4.3 MB)


route -n

```
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```


cat /etc/resolv.conf

```
search atsamadrid.lan
nameserver 192.168.1.2

```

sudo iptables -L -vnx

```
Chain INPUT (policy ACCEPT 175641 packets, 34214912 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 445777 packets, 102832291 bytes)
    pkts      bytes target     prot opt in     out     source               destination         

```

So, this is it.

Any ideas?

Thanks a lot,

   Best regards,

      phasel

---

### Post by SpaceTeddy on 2008-06-27
first off, sorry for the wait.

I kept re-reading the post and trying to make heads or tails of it. Unfortunately, i cannot make out anything that would explain this behavior. I have two ideas, but both are so far fetched that they are highly unlikely. The network setup itself looks perfectly normal. 

The only ideas i have are these:
1.) there is another computer that uses the IP 192.168.1.45 and overwrites the arp cache. That would explain the behavior... really. But that other computer should be on the same network, and should have the same problem as well
2.) Your Networkcard on the client is broken. But this is rules out by the system being able to do this with other OS's. So that only leaves the driver of the network card... which is highly improbable... 

I'll keep thinking about this, but right now i am not seeing any solution or even the idea that would lead to a solution.

sorry to disappoint.

---

### Post by superprash2003 on 2008-06-27
this may sound stupid but you could try changing dns servers to opendns .. ips are 208.67.222.222 and 208.67.220.220 .. also are you connected via usb or LAN?

---

### Post by phasel on 2008-06-27
Thanks a lot for your suggestions. I had already thought about the ethernet card, but it would certainly be complicated as other pc's have no problems... Anyway, I will install a second network card, and connect that one, let's see if problems persist.
With respect to other pc with the same ip address, I also discard it, because I have tried using dhcp, fixed address, connecting with wire, and wireless, and the problem is there always. When I connect wirelessly, I get a different IP address.

Anyway... If I cannot solve it, I will reinstall the server. First time was complicated, but now it is just a matter of saving the /etc folder :)

Thanks again,

  Best regards,

      phasel

---

### Post by plewisfdx on 2008-06-27
To rule out DNS, try ping and ssh with ip address AND hostname, and see if either works.

---

### Post by Iowan on 2008-06-27
Did you turn off the firewall (UFW) that came enabled by default?

---

### Post by phasel on 2008-06-28
Thanks for the new comments. Unfortunately, it has nothing to do with DNS. In the lan, I ssh and ping with the ip address.

With respect to the firewall, it is in default allow, which I think is just like being disable.

Next week, I will try the new ethernet. I am completely lost. I even tried disconnecting all the windows pc's from the lan thinking a virus might be causing this behaviour, but after a promising ping, half an hour later I could not connect again...

Thanks again, and have a nice weekend. At least, looking around I'm learning quite a few things... ;)

Best regards,

  phasel

---

### Post by phasel on 2008-07-06
OK,

Putting a new network card solved the problem. So far it is OK for me. I am almost sure that the problems are due to some hardware control in the card.
I will investigate, whenever I have a low work afternoon (maybe in August ;)
Anyway, as it is working now in eth1, I can leave it for some time.

Thanks all anyway. I might end up calling Dell to check if they have any idea.

 Best regards,

       phasel

---

