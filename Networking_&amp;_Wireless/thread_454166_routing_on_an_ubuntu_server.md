---
title: "routing on an ubuntu server"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by Flix83 on 2007-05-25
Hello,
I am running a little LAN over here and I have setup an Ubuntu 7.04 Samba Fileserver. It has a wireless connection for which he gets an ip from the DSL Router, there are other People in the Wireless Network which should (and can) excess Files on the Server. My Workstation is connected over Ethernet and the Server should route the traffic into the wireless network, but he doesn't. I am now using firestarter but I don't need a firewall in this net. I think this problem can be solved by using kernel routing tables, but I am a total noob to them.
here is my connfiguration, which doesnt work yet.

flix@Bateman:~$ ifconfig
eth0      Protokoll:Ethernet  Hardware Adresse 00:08:54:D0:83:DA
          inet Adresse:192.168.5.1  Bcast:192.168.5.255  Maske:255.255.255.0
          inet6 Adresse: fe80::208:54ff:fed0:83da/64 GÃ¼ltigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33042678 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33098897 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000
          RX bytes:2296439939 (2.1 GiB)  TX bytes:1460611262 (1.3 GiB)
          Interrupt:16 Basisadresse:0x6f00

lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 GÃ¼ltigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:292 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:0
          RX bytes:27496 (26.8 KiB)  TX bytes:27496 (26.8 KiB)

wlan0     Protokoll:Ethernet  Hardware Adresse 00:30:F1:71:7D:AE
          inet Adresse:192.168.2.32  Bcast:192.168.2.255  Maske:255.255.255.0
          inet6 Adresse: fe80::230:f1ff:fe71:7dae/64 GÃ¼ltigkeitsbereich:Verbindung
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:19080 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13151 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 SendewarteschlangenlÃ¤nge:1000
          RX bytes:22258093 (21.2 MiB)  TX bytes:1597590 (1.5 MiB)

flix@Bateman:~$ route
Kernel IP Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.5.1     *               255.255.255.255 UH    0      0        0 eth0
192.168.2.32    *               255.255.255.255 UH    0      0        0 wlan0
192.168.5.0     192.168.5.1     255.255.255.0   UG    0      0        0 eth0
192.168.5.0     *               255.255.255.0   U     0      0        0 eth0
192.168.2.0     192.168.2.32    255.255.255.0   UG    0      0        0 wlan0
192.168.2.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
flix@Bateman:~$

Please excuse my bad english!

---

### Post by gustavoberman on 2007-05-25
maybe it is not enabled as a router
check this
cat /proc/sys/net/ipv4/ip_forward
if it is 0 then the router is not set
do:
echo 1 > /proc/sys/net/ipv4/ip_forward
to enable it

---

### Post by Flix83 on 2007-05-27
The routing is enabled but it isn't working, do I need a DNS server on that box and what DNS and Gateway data shall the DHCP Server distribute?

---

### Post by Austin_KW on 2007-05-27
What traffic do you need routed? Is your workstation directly connected to the server?

---

### Post by Flix83 on 2007-05-27
Does that make a diffrence? I want to use anything e. g. SMB, http, ftp, ICQ. 
The Workstation is connected over a normal Ethernetswitch other clients should be able to connect through the switch too.

---

### Post by Austin_KW on 2007-05-27
A switch is fine, I was only thinking about another router between the two.

Firestarter may do it all for you.
If you tell firestarter to share the wireless as the internet connection and the ethernet interface as the client connection. You can also enable the mini dhcp server in firestarter and it will automatically setup you workstation ip address and default routes.

Use the firestarter wizzard to set it up, but I think that it will then allow your workstation to connect out but not to the servers on the server. You will have to add rules to allow you workstation to access ports SMB, etc, on the servers ethernet port.

But is there a reason for not connecting the switch to your dsl router and having everything on the same subnet.

Alternatively you could put everything on the same subnet and bridge the ethernet and wireless interfaces on the server.

---

### Post by Flix83 on 2007-05-27
I know that firestarter is working quite well, I'm using it for 4 weeks know, but I need X and a logged on User for it to work. (A friend of mine always said: "There is no X in Server!") ;-) I have already setup the standard DHCP Server on the Box and I am wondering which Gateway and DNS Server he should anounce. 
Normaly I would prefer to plug the DSL Router into one NIC and turn of the firewall and everything on the DSL Router and setup another network on another NIC with a Firewall and everything on the Linux Server. This is not possible because I am sharing the Internetconnection with another flat (the owner knows and she is getting paid) and there is no way to get a cable from that flat into mine.

---

### Post by Austin_KW on 2007-05-27
I have only ever used it interactively, when I wanted to temporarily share a connection etc.

But my understanding was that firestarter was just a gui used to configure the IP tables. I thought that it did this by building a script that was run when firestarter was started.

Have you tried "sudo  /etc/firestarter/firestarter.sh start"  

If this works then you could add it to /etc/rc.local to be run at the end of boot sequence.

---

