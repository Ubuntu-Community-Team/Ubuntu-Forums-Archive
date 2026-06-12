---
title: "Forwarding Problem"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by Coldbird on 2008-03-07
I checked the NAT / IP Masquerading Wiki for Ubuntu to get my PS2 online and hooked up...
I thought - all working fine and dandy... right after I added the few commands from the Wiki...

But the horror followed soon after... I rebooted... Now both my PS2 and PC can't access the Web in any way anymore... I'm writing this using a external HDD with Windows installed onto it...

I checked the routing list using the command "routel"... What appeared quite fishy to me was that there was a route that had my Internet Address as Source AND Target... It was also set at kernel level - unlike a few other routes...

And the message of my dialing script (Speedtouch 330 USB Modem) was saying something about a default route not being overwritten... and I got the guess that the route i found is this "default route"...

Thus I'm asking... how can I fully wipe the routing list? Like set it back to the way it was before?
routef for flushing wont do anything... not minding if sudo'ed or not.

I'm desperate... thanks in advance.

---

### Post by HermanAB on 2008-03-07
Not easy, since you got to give route enough of a clue to know which route to delete.  It would have been easy if the routes were numbered, but they aren't.

$ man route

$ route del yadda yadda

---

### Post by Coldbird on 2008-03-08
routel command doesnt give me a numbered list really...
you could give me a "working" del command example maybe? like with all arguments needed?

routel only outputs me a list with target source device etc... but nothing like any numbers to go with...

im awaiting your input. thanks in advance.

---

### Post by Iowan on 2008-03-08
> **Coldbird said:**
> I checked the routing list using the command "routel"...
Try it with the **route** command. The **man** page for **route** gives examples - (per HermanAB's suggestion.)

---

### Post by Coldbird on 2008-03-09
[http://img177.imageshack.us/img177/6499/outofideastj0.jpg](http://img177.imageshack.us/img177/6499/outofideastj0.jpg)
the problem remains... the only ip i can ping is my isp's server ip... domain names wont resolve it seems... even thought dns is fine... and i already tried playing around with route... but as you can see it tells me theres nothing to play around with...

so im at the beginning again... i screenshotted some commands - that i personally think might be useful for other people to figure out whats causing my problem...

i probably repeat myself but the last thing i did was doing the NAT tutorial on the ubuntu wiki to share my inet with my ps2... worked fine while i was still online... but after a pc reboot it farked up...

---

### Post by SpaceTeddy on 2008-03-10
can you please provide the output of the following commands to see if your basic configuration is right ?
> ifconfig
route -n
iptables -L --table nat
cat /etc/network/interfaces

---

### Post by Coldbird on 2008-03-10
ifconfig
```
ath0      Protokoll:Ethernet  Hardware Adresse 00:16:CE:5D:BD:4D  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Protokoll:Ethernet  Hardware Adresse 00:16:D4:13:04:19  
          inet Adresse:192.168.0.1  Bcast:192.168.0.255  Maske:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Basisadresse:0x6800 

lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:4728 (4.6 KB)  TX bytes:4728 (4.6 KB)

ppp0      Protokoll:Punkt-zu-Punkt Verbindung  
          inet Adresse:85.124.100.64  P-z-P:213.229.45.251  Maske:255.255.255.255
          UP PUNKTZUPUNKT RUNNING NOARP MULTICAST  MTU:1460  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:3 
          RX bytes:162 (162.0 b)  TX bytes:87 (87.0 b)

wifi0     Protokoll:UNSPEC  Hardware Adresse 00-16-CE-5D-BD-4D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:1387
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:199 
          RX bytes:390 (390.0 b)  TX bytes:4462 (4.3 KB)
          Interrupt:17 


```
interfaces
```
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.0.1

```
route -c
```
Kernel IP Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
213.229.45.251  0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0

```
i didnt provide iptables cause all three rows were empty... nothing to see...

---

### Post by SpaceTeddy on 2008-03-10
by the looks of this, i'd take it that ppp0 is your internet device (the only one having an internet ip address :) )

the problem is that eth0 overwrites the default gateway, which then cannot be set by the pppd process when the connection gets established.
to fix this, try removing the gateway line from your static eth0 definition (you cannot really be your own default gateway anyway) in the /etc/network/interfaces. Then restart your computer. 
If you do not wish to restart, manually remove the default gateway with this command

```
sudo route del -net 0.0.0.0
```

and then add the correct one (which is the point-to-point partner of your your ppp0 device) with this command
```
sudo route add default gw 213.229.45.251
```

or, maybe even this works (not sure, but that way you do not have to worry about the remote ip address)
```
sudo route add default gw dev ppp0
```

i hope from the examples you can make your internet work again :)

---

### Post by The Cog on 2008-03-10
I see an immediate problem here in that your default gateway is yourself. This is what's configured in /etc/network/interfaces, so its a configuration issue. The default route should point to the IP address of the next hop along the way towards the internet, which is presumably the other end of the ppp0 interface.

I don't know how to correst that configuration, but I think the default route is the immediate problem.

EDIT:
Oops, looks like SpaceTeddy beat me to it and knows the fix too.

---

### Post by Coldbird on 2008-03-10
I thank you both very much - You saved a cold birds' day.

---

