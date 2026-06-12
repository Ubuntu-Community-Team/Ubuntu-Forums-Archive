---
title: "My Wifi works, it connects but doesnt get an ip, please help me."
date: 2006-10-05
forum: Networking &amp; Wireless
---

### Post by Yuzem on 2006-10-05
I cant connect to the internet with my wifi.
It was a nightmare to get where i am. To get my wifi working i had to reinstall ubuntu several times, i have tried ndiswraper, wifi-radar, some old drivers that didnt work.
I dont know whats wrong...

This is my setup:
(Cable Modem) --> (Pc1 XP)(Wifi) <--> (Wifi)(Pc2 Ubuntu)

I have XP on another partition in the Pc2 and internet works perfectly fine.
My wifi card uses the atmel chip. I have installed the latest drivers (0.14beta1) and firmware. Its seems to work just fine.

"iwlist wlan0 scan" gave me this:
```

wlan0     Scan completed :
          Cell 01 - Address: 02:00:8D:8A:2C:31
                    ESSID:"wert"
                    Mode:Ad-Hoc
                    Channel:6
                    Encryption key:off
                    Quality:0/0  Signal level:28/255  Noise level:0/0
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s

```
"sudo iwconfig wlan0" gave me:
```

wlan0     IEEE 802.11-DS  ESSID:"wert"  Nickname:"wert"
          Mode:Ad-Hoc  Frequency:2.437 GHz  Cell: 02:00:8D:8A:2C:31
          Bit Rate:11 Mb/s   Tx-Power=15 dBm
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B
          Encryption key:off
          Power Management:off
          Link Quality=0/0  Signal level=70/255  Noise level=0/0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
"sudo dhclient wlan0" gave me this:
```

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:80:48:22:dd:92
Sending on   LPF/wlan0/00:80:48:22:dd:92
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
I need help please. I really really really want to make the switch to linux.

---

### Post by Yuzem on 2006-10-06
If Windows XP works why Ubuntu doesnt?
Could it be the beta drivers?

---

### Post by Yuzem on 2006-10-07
Anyone?
Please!

---

### Post by glug101 on 2006-10-08
Until about 5 minutes ago, I had the same issue.  Drivers were loaded in the kernel, iwlist found my router, but I was unable to connect through dhcp.  Well, I have an inelligant solution to it.

Scrap DHCP, and just plug in the address manually.  Just make sure that your DHCP router knows about this.  You wouldn't want your router assigning that same IP to another computer;) (choosing the same ip that gets assigned to you under windows should work fine)

Admittedly, this is not the solution I would like (DHCP should work) but it worked for me.  Hope this helps.

P.S.  Hang in there with linux, after the initial learning curve and brick walls, there are a lot of advantages to using open source software;)

---

### Post by the_one on 2006-10-10
Looks like you're using your XP box as a gateway. When you set up Internet Connection sharing in XP the DHCP service is started to assign IPs. You have to do the same thing manually under Linux.
Other wise you can do the fixed IP method mentioned earlier.
I've never done this myself...maybe someone else has...Hope this helps.

---

### Post by the_one on 2006-10-10
Oops...sorry. I misunderstood your post...thought you had Linux on Pc1.

Fixed IP seems to be the only way to go...
[http://www.annoyances.org/exec/show/ics_other](http://www.annoyances.org/exec/show/ics_other)

---

### Post by Yuzem on 2006-10-10
Thanks a lot to both for your answers.
Still cant connect but i think that i am closer now. (ping google.com takes more time to return "ping: unknown host google")
Before it was instantaneous.
I only have two computer. I think there will be no problems with assigning the same IP to another computer.

In xp "ipconfig /all" gave me this:
```

Configuración IP de Windows

        Nombre del host . . . . . . . . . : asd
        Sufijo DNS principal  . . . . . . :
        Tipo de nodo. . . . . . . . . . . : mixto
        Enrutamiento habilitado. . . . . .: No
        Proxy WINS habilitado. . . . .    : No
        Lista de búsqueda de sufijo DNS:    mshome.net

Adaptador Ethernet Conexiones de red inalámbricas          :

        Sufijo de conexión específica DNS : mshome.net
        Descripción. . . . . . . . . . .  : Compex iWavePort WLU11A Mod2
        Dirección física. . . . . . . . . : 00-80-48-22-DD-92
        DHCP habilitado. . . . . . . . .  : No
        Autoconfiguración habilitada. . . : Sí
        Dirección IP. . . . . . . . . . . : 192.168.0.81
        Máscara de subred . . . . . . . . : 255.255.255.0
        Puerta de enlace predeterminada   : 192.168.0.1
        Servidor DHCP . . . . . . . . . . : 192.168.0.1
        Servidores DNS . . . . . . . . . .: 192.168.0.1
        Concesión obtenida . . . . . . .  : Martes, 10 de Octubre de 2006 10:46:
00 a.m.
        Concesión expira . . . . . . . . .: Martes, 17 de Octubre de 2006 10:46:
00 a.m.

```

My "interfaces" file is:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

mapping hotplug
script grep
map wlan0

iface wlan0 inet static
wireless-essid wert
wireless_mode ad-hoc

# address 192.168.1.3 OR REPLACE WITH YOUR FIXED IP ADDRESS
netmask 255.255.255.0
network 192.168.0.37
# broadcast 
gateway 192.168.0.1
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 192.168.0.1

auto wlan0
```



And this is what i am getting in Ubuntu:
```
azd@asd:~$ sudo ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:251 errors:0 dropped:0 overruns:0 frame:0
          TX packets:251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:20276 (19.8 KiB)  TX bytes:20276 (19.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:80:48:22:DD:92
          inet addr:192.168.0.37  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16289 (15.9 KiB)  TX bytes:168 (168.0 b)

azd@asd:~$ ping google
ping: unknown host google
azd@asd:~$
```

I think that something is wrong but what is it?

---

### Post by Yuzem on 2006-10-12
If is needed i can translate to english my "ipconfig /all" result.

---

### Post by the_one on 2006-10-13
Sorry I took so long to reply.

First....there are a few things that are wrong. Basically...your wifi card is not passing request from your Ubuntu box to the cable modem.

Your XP "ipconfig" doesn't show your cable modem IP. ..how is it connected? Your need your cable modem IP for your XP ICS settings.


Next...

Adaptador Ethernet Conexiones de red inalámbricas          :

        Sufijo de conexión específica DNS : mshome.net
        Descripción. . . . . . . . . . .  : Compex iWavePort WLU11A Mod2
        Dirección física. . . . . . . . . : 00-80-48-22-DD-92
        DHCP habilitado. . . . . . . . .  : No
        Autoconfiguración habilitada. . . : Sí
        Dirección IP. . . . . . . . . . . : 192.168.0.81 [COLOR="Blue"]<---This is your internal Network IP so...192.168.0.1[/COLOR]
        Máscara de subred . . . . . . . . : 255.255.255.0 [COLOR="Blue"]<---you can limit the number of IP adresses here...
EX. 255.255.255.248 gives you 5 IP adresses 
255 - 248 = 7 - 1 (gateway IP) - 1 (broadcast IP) = 5
Its up to you if you want to change it.[/COLOR]
        Puerta de enlace predeterminada   : 192.168.0.1  [COLOR="Blue"]<---cable modem IP[/COLOR]
        Servidor DHCP . . . . . . . . . . : 192.168.0.1  [COLOR="Blue"]<---none (leave it blank)...you have static IP[/COLOR]
        Servidores DNS . . . . . . . . . .: 192.168.0.1  [COLOR="Blue"]<--cable modem IP[/COLOR]


The Ubuntu "interfaces" looks good. Just make sure the subnet mask (Máscara de subred) is the same as your XP wifi.
With 255.255.255.248 mask your IP range is 192.168.0.2 - 192.168.0.6
So "network 192.168.0.37" in Ubuntu could be changed to, for example 192.168.0.3

That should do it....

---

### Post by Yuzem on 2006-10-14
Thanks again for your answer. Still cant connect.
I have tried what you told me with no luck.
This is what i am doing:
sudo gedit /etc/modules/interfaces
(then i edit and save the file)
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo ifconfig
ping google.com

I have tried different values and nothing works...
For example, with the following config:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

mapping hotplug
script grep
map wlan0

iface wlan0 inet static
wireless-essid wert
wireless_mode ad-hoc

address 192.168.0.100
netmask 255.255.255.248
network 192.168.0.3
# network 192.168.0.81
# broadcast 
gateway 192.168.0.1
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 192.168.0.1

auto wlan0
```

I get this:
```
azd@asd:~$ sudo ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:423 errors:0 dropped:0 overruns:0 frame:0
          TX packets:423 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:38360 (37.4 KiB)  TX bytes:38360 (37.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:80:48:22:DD:92
          inet addr:192.168.0.37  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2519 (2.4 KiB)  TX bytes:0 (0.0 b)

azd@asd:~$ ping google.com
ping: unknown host google.com

```
I cant use ubuntu without internet and i really want to.
I am up for try and try and try and try... but i dont know what to try...
Any advice is welcome.
Thanks in advance.

---

### Post by the_one on 2006-10-14
address 192.168.0.100 [COLOR="Blue"]<---IP (192.168.0.3) goes here...[/COLOR]
netmask 255.255.255.248
network 192.168.0.3 [COLOR="Blue"]<---Not here...I don't think you need to put any thing here[/COLOR]
# network 192.168.0.81
# broadcast 
gateway 192.168.0.1
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 192.168.0.1


wlan0     Link encap:Ethernet  HWaddr 00:80:48:22:DD:92
          inet addr:192.168.0.37  Bcast:192.168.0.255  Mask:255.255.255.0 [COLOR="Blue"]<---This shows that your device is not accepting the settings.[/COLOR]


Before you ping google, try to ping your XP box at 192.168.0.1 (you can use IP addresses in the ping command). 
You should ping from closest IP first and work you way out to the internet to see where the broken link is.
So....
XP wifi interface IP
XP cable modem interface IP
ISP (if you know their IP)
Google, Yahoo, What ever

The ping command works a little different in Linux.
You have to put "wlan0" in there somewhere
> ping --help


You can use these commands to manually set your client.

> sudo ifconfig wlan0 down
sudo ifconfig wlan0 192.168.0.3 netmask 255.255.255.248 up

or
> sudo ifconfig wlan0 ip addr 192.168.0.3 netmask 255.255.255.248 up
> sudo route add default gw 192.168.0.1
sudo ifconfig wlan0


By the way, here is a guide for using the GUI to make settings instead of editing your files.

[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)

---

### Post by Yuzem on 2006-10-15
I really sorry but my bad luck continue. ](*,)
I tried to follow your indications:
```
azd@asd:~$ sudo ifconfig
Password:
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8612 (8.4 KiB)  TX bytes:8612 (8.4 KiB)

azd@asd:~$ sudo ifconfig wlan0 down
azd@asd:~$ sudo gedit /etc/network/interfaces
```
I edited "interfaces":
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

mapping hotplug
script grep
map wlan0

iface wlan0 inet static
wireless-essid wert
wireless_mode ad-hoc

address 192.168.0.3
netmask 255.255.255.248
# network 192.168.0.81
# broadcast
gateway 192.168.0.1
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 192.168.0.1

auto wlan0
```
In terminal:
```
azd@asd:~$ sudo ifconfig wlan0 up
azd@asd:~$
azd@asd:~$
azd@asd:~$
azd@asd:~$
azd@asd:~$
azd@asd:~$
azd@asd:~$
azd@asd:~$
azd@asd:~$
azd@asd:~$
azd@asd:~$ sudo ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8712 (8.5 KiB)  TX bytes:8712 (8.5 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:80:48:22:DD:92
          inet6 addr: fe80::280:48ff:fe22:dd92/64 Scope:Link
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:168 (168.0 b)

azd@asd:~$ ping 192.168.0.1
connect: Network is unreachable
```
Then i check Network:
[[IMG]http://img208.imageshack.us/img208/1980/pantallazopropiedadesdelinterfazml1.th.png[/IMG]](http://img208.imageshack.us/my.php?image=pantallazopropiedadesdelinterfazml1.png)
Again in terminal:
```
azd@asd:~$ sudo ifconfig wlan0 192.168.0.3 netmask 255.255.255.248 up
azd@asd:~$ sudo ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:80:48:22:DD:92
          inet addr:192.168.0.3  Bcast:192.168.0.7  Mask:255.255.255.248
          inet6 addr: fe80::280:48ff:fe22:dd92/64 Scope:Link
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:168 (168.0 b)

azd@asd:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.3 icmp_seq=1 Destination Host Unreachable
From 192.168.0.3 icmp_seq=2 Destination Host Unreachable
From 192.168.0.3 icmp_seq=3 Destination Host Unreachable
From 192.168.0.3 icmp_seq=5 Destination Host Unreachable
From 192.168.0.3 icmp_seq=6 Destination Host Unreachable
From 192.168.0.3 icmp_seq=7 Destination Host Unreachable
From 192.168.0.3 icmp_seq=9 Destination Host Unreachable
From 192.168.0.3 icmp_seq=10 Destination Host Unreachable
From 192.168.0.3 icmp_seq=11 Destination Host Unreachable
From 192.168.0.3 icmp_seq=13 Destination Host Unreachable
From 192.168.0.3 icmp_seq=14 Destination Host Unreachable
From 192.168.0.3 icmp_seq=15 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
16 packets transmitted, 0 received, +12 errors, 100% packet loss, time 15035ms
, pipe 3
azd@asd:~$ sudo ifconfig wlan0 ip addr 192.168.0.3 netmask 255.255.255.248 up
ip: Host name lookup failure
ifconfig: `--help' gives usage information.
azd@asd:~$ sudo route add default gw 192.168.0.1
azd@asd:~$ sudo ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:80:48:22:DD:92
          inet addr:192.168.0.3  Bcast:192.168.0.7  Mask:255.255.255.248
          inet6 addr: fe80::280:48ff:fe22:dd92/64 Scope:Link
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:168 (168.0 b)

azd@asd:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.3 icmp_seq=2 Destination Host Unreachable
From 192.168.0.3 icmp_seq=3 Destination Host Unreachable
From 192.168.0.3 icmp_seq=4 Destination Host Unreachable
From 192.168.0.3 icmp_seq=6 Destination Host Unreachable
From 192.168.0.3 icmp_seq=7 Destination Host Unreachable
From 192.168.0.3 icmp_seq=8 Destination Host Unreachable
From 192.168.0.3 icmp_seq=10 Destination Host Unreachable
From 192.168.0.3 icmp_seq=11 Destination Host Unreachable
From 192.168.0.3 icmp_seq=12 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
12 packets transmitted, 0 received, +9 errors, 100% packet loss, time 11008ms
, pipe 3
```
Any suggestion is welcome.
Thanks again.

---

### Post by louistan3 on 2006-10-15
yuzem.. how come you need to pass thru the xp box to access the wifi? cant you connect straight to the wifi router? 

and if with your current setup you can ping the xp box.. you might wana try pinging your router.. then if you can ping the router.. but not google or yahoo.. you could check if your DNS settings are correct.. :D hope this helps..

---

### Post by Yuzem on 2006-10-15
Thanks louistan3, but i dont have a router.
My setup is:
(Cable Modem) --> (Pc1 XP)(Wifi) <--> (Wifi)(Pc2 Ubuntu)

I also have XP in Pc2 and it doesn't has any problem.

---

### Post by the_one on 2006-10-17
Try turning off windows firewall.

Try adding the whole lot...

> sudo ifconfig wlan0 192.168.0.3 netmask 255.255.255.248
sudo iwconfig wlan0 ESSID wert mode managed
I think you want "managed" rather than "ad-hoc".

This comes from SUSE forums.
> Leave "dns-nameservers" in "Interfaces" blank
Edit /etc/resolv.conf 
Make sure the "domain" entry has your windows workgroup name and add two nameserver entries.
Ex.
nameserver xxx.xxx.xxx.xxx (Primary DNS)
nameserver xxx.xxx.xxx.xxx (Secondary DNS)
These are your ISP's DNS servers. Your ISP's documentation or support web pages should have that information.

louistan3 is right...using a router is the easiest way, except if your connection to your cable modem is USB. I got a Netgear DG834 router for $20.00(US).

---

### Post by Yuzem on 2006-10-17
Windows firewall is off. I am using Sygate.
I think that my wifi doesn't support managed. I will try any way.
This is what i did:
I edited interfaces ("dns-nameservers" isn't set now):
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

mapping hotplug
script grep
map wlan0

iface wlan0 inet static
wireless-essid wert
wireless_mode ad-hoc

address 192.168.0.3
netmask 255.255.255.248
# network 192.168.0.81
# broadcast
gateway 192.168.0.1
# dns-* options are implemented by the resolvconf package, if installed
# dns-nameservers 192.168.0.1

auto wlan0
```

I edited resolv.conf:
```
domain WERT
nameserver 200.115.192.29
nameserver 200.115.192.30
```

In terminal:
```
azd@asd:~$ sudo ifconfig wlan0 down
azd@asd:~$ sudo ifconfig wlan0 up
azd@asd:~$
azd@asd:~$
azd@asd:~$
azd@asd:~$
azd@asd:~$
azd@asd:~$
azd@asd:~$
azd@asd:~$
azd@asd:~$
azd@asd:~$
azd@asd:~$ sudo ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:11556 (11.2 KiB)  TX bytes:11556 (11.2 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:80:48:22:DD:92
          inet addr:192.168.0.37  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10601 (10.3 KiB)  TX bytes:0 (0.0 b)

azd@asd:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.37 icmp_seq=1 Destination Host Unreachable
From 192.168.0.37 icmp_seq=2 Destination Host Unreachable
From 192.168.0.37 icmp_seq=3 Destination Host Unreachable
From 192.168.0.37 icmp_seq=5 Destination Host Unreachable
From 192.168.0.37 icmp_seq=6 Destination Host Unreachable
From 192.168.0.37 icmp_seq=7 Destination Host Unreachable
From 192.168.0.37 icmp_seq=9 Destination Host Unreachable
From 192.168.0.37 icmp_seq=10 Destination Host Unreachable
From 192.168.0.37 icmp_seq=11 Destination Host Unreachable
From 192.168.0.37 icmp_seq=13 Destination Host Unreachable
From 192.168.0.37 icmp_seq=14 Destination Host Unreachable
From 192.168.0.37 icmp_seq=15 Destination Host Unreachable
From 192.168.0.37 icmp_seq=16 Destination Host Unreachable
From 192.168.0.37 icmp_seq=17 Destination Host Unreachable
From 192.168.0.37 icmp_seq=18 Destination Host Unreachable
From 192.168.0.37 icmp_seq=20 Destination Host Unreachable
From 192.168.0.37 icmp_seq=21 Destination Host Unreachable
From 192.168.0.37 icmp_seq=22 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
22 packets transmitted, 0 received, +18 errors, 100% packet loss, time 21037ms
, pipe 3
```

Again in terminal:
```
azd@asd:~$ sudo ifconfig wlan0 192.168.0.3 netmask 255.255.255.248
azd@asd:~$ sudo ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13672 (13.3 KiB)  TX bytes:13672 (13.3 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:80:48:22:DD:92
          inet addr:192.168.0.3  Bcast:192.168.0.7  Mask:255.255.255.248
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10601 (10.3 KiB)  TX bytes:0 (0.0 b)

azd@asd:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.3 icmp_seq=1 Destination Host Unreachable
From 192.168.0.3 icmp_seq=2 Destination Host Unreachable
From 192.168.0.3 icmp_seq=3 Destination Host Unreachable
From 192.168.0.3 icmp_seq=5 Destination Host Unreachable
From 192.168.0.3 icmp_seq=6 Destination Host Unreachable
From 192.168.0.3 icmp_seq=7 Destination Host Unreachable
From 192.168.0.3 icmp_seq=9 Destination Host Unreachable
From 192.168.0.3 icmp_seq=10 Destination Host Unreachable
From 192.168.0.3 icmp_seq=11 Destination Host Unreachable
From 192.168.0.3 icmp_seq=13 Destination Host Unreachable
From 192.168.0.3 icmp_seq=14 Destination Host Unreachable
From 192.168.0.3 icmp_seq=15 Destination Host Unreachable
From 192.168.0.3 icmp_seq=17 Destination Host Unreachable
From 192.168.0.3 icmp_seq=18 Destination Host Unreachable
From 192.168.0.3 icmp_seq=19 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
20 packets transmitted, 0 received, +15 errors, 100% packet loss, time 19038ms
, pipe 3
```

The last attempt:
```
azd@asd:~$ sudo iwconfig wlan0 ESSID wert mode managed
azd@asd:~$ sudo ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15464 (15.1 KiB)  TX bytes:15464 (15.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:80:48:22:DD:92
          inet addr:192.168.0.3  Bcast:192.168.0.7  Mask:255.255.255.248
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10601 (10.3 KiB)  TX bytes:0 (0.0 b)

azd@asd:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.3 icmp_seq=2 Destination Host Unreachable
From 192.168.0.3 icmp_seq=3 Destination Host Unreachable
From 192.168.0.3 icmp_seq=4 Destination Host Unreachable
From 192.168.0.3 icmp_seq=6 Destination Host Unreachable
From 192.168.0.3 icmp_seq=7 Destination Host Unreachable
From 192.168.0.3 icmp_seq=8 Destination Host Unreachable
From 192.168.0.3 icmp_seq=10 Destination Host Unreachable
From 192.168.0.3 icmp_seq=11 Destination Host Unreachable
From 192.168.0.3 icmp_seq=12 Destination Host Unreachable
From 192.168.0.3 icmp_seq=14 Destination Host Unreachable
From 192.168.0.3 icmp_seq=15 Destination Host Unreachable
From 192.168.0.3 icmp_seq=16 Destination Host Unreachable
From 192.168.0.3 icmp_seq=18 Destination Host Unreachable
From 192.168.0.3 icmp_seq=19 Destination Host Unreachable
From 192.168.0.3 icmp_seq=20 Destination Host Unreachable
From 192.168.0.3 icmp_seq=22 Destination Host Unreachable
From 192.168.0.3 icmp_seq=23 Destination Host Unreachable
From 192.168.0.3 icmp_seq=24 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
24 packets transmitted, 0 received, +18 errors, 100% packet loss, time 23021ms
, pipe 3
```

Where i am a router isn't so cheap and Ubuntu should be able to do this.
I wonder if Edgy will fix this problem.
Is there anything else I could do?
Thanks in advance.

---

### Post by the_one on 2006-10-17
Well Yuzem I'm just about out of ideas. Going to edgy won't help.
your Linux side is working just fine. It just can't find your Xp IP.
Try using wifi-radar to scan for your XP box and see if it shows up. I think you can connect to it through wifi-radar. At lest you can see if the ESSID shows up and check the IP address it has.

I haven't used Windows ICS since Win98 and NT4 days. It's quirky and not very well documented.

Doesn't Sygate have built-in connection sharing? I used an ancient version quite a few years ago and it had connection sharing that worked better than windows ics. Of course, I wasn't using Linux then either.

Common you linux gurus!.... feel free to jump in on this.:-k

---

### Post by Yuzem on 2006-10-18
Maybe Edgy will fix the problem with DHCP(If there is a problem)
If XP works and Ubuntu not... it sounds like there is a problem with Ubuntu.

I have already tried wifi-radar and with dhcp enable it connects and shows the ESSID but doesn't get an ip. With static ip it connects and gets the  pre configured ip but there is no internet.

I have Sygate Personal Firewall and the version that has ICS is Sygate Home Network.

Just in case the problem could be some kind of incompatibility with windows ICS i will try other DHCP server for windows.

---

### Post by the_one on 2006-10-19
IMO Ubuntu is making the connection but XP is either not responding to Ubuntu or not passing the traffic to your cable modem. That's why I said to turn of the firewall.

Unless it is noted in the change log for Edgy, DHCP will be the same as Dapper. So I wouldn't suggest upgrading, unless you're just curious.:) DHCP is OS agnostic, it should assign an IP to anything that requests one (network printer, NAS, Tivo, etc.).

You were right...ad-hoc is wireless card-to-card, like wired NIC-to-NIC connection.

I went to numerous forums and the results were varied. Some had success with DHCP enabled, others say static IP is the only way to go. A couple say you have to have Samba installed.

I bet if you go out and find another open access point Ubuntu will connect.

Try going back to DHCP (since this since the simplest to work with) and use Wifi-Radar again. Wifi-Radar will make the connection if it is at all possible.

I'm still migrating from Windows so I try to avoid editing Linux config files if there is a GUI method available. I started with DOS so I'm not affaid if the command line, I'm just such a terrible typist that it take me forever to type a line without typos (the backspace is my constant companion).

I know you've tried this already, but give it another try.

1. Wipe and do a fresh Ubuntu install. Don't re-install over the existing one. Delete the partition (if you can) and reformat.

2. Go through the XP ICS setup and use DHCP.

3. Use Network Manager to set your wifi card for DHCP.

3. Use Wifi-Radar to find and connect to the XP ESSID that it finds.

This is the simplest method and should work.


Right again about Sygate...I was using it before it was called "Home Network". I think it was called "WinGate". I think Kerio still has a proxy server in their Personal Firewall package (free). You might want to give that a try on your XP box, if you don't mind changing firewalls. The firewall is lightweight, unobtrusive, robust and feature rich (my choice over Zone Alarm).

That's all I have....sorry I couldn't be more help.
Good Luck.

---

### Post by Yuzem on 2006-10-19
Well, thanks a lot for all the help you have given to me.
I have tried different dhcp servers for windows but i could not make them work.
I will format the partition and reinstall Ubuntu but i will wait to the next week for Edgy.
I was going to install Edgy anyway.
I will install samba and see what happens.
Thanks again.
Have a nice weekend.

---

