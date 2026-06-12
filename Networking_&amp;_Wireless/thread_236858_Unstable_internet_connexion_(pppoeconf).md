---
title: "Unstable internet connexion (pppoeconf)"
date: 2006-08-15
forum: Networking &amp; Wireless
---

### Post by crobard on 2006-08-15
Hi all,

I have a problem with my internet connexion. I configured my ppp connexion with pppoeconf and requested to start my connexion at boot. This is never the case and I have to run poff -a and pon dsl-provider to start my internet connexion each time I reboot my computer. I have an Alcatel Speed Touch Home ADSL modem with Ethernet access. My modem is configured as DHCP server.

Here is my ifconfig when the internet connexion is down :

eth0      Lien encap:Ethernet  HWaddr 00:02:E3:14:5C:85
          inet adr:10.0.0.1  Bcast:10.255.255.255  Masque:255.0.0.0
          adr inet6: fe80::202:e3ff:fe14:5c85/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:88 erreurs:0 :0 overruns:0 frame:0
          TX packets:159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:7281 (7.1 KiB) Octets transmis:12468 (12.1 KiB)
          Interruption:185 Adresse de base:0x8000

lo        Lien encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:23 erreurs:0 :0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reçus:1319 (1.2 KiB) Octets transmis:1319 (1.2 KiB)

ppp0      Lien encap:Protocole Point-à-Point
          inet adr:XX.XX.XX.XX  P-t-P:XX.XX.XX.XX  Masque:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          Packets reçus:45 erreurs:0 :0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:3
          Octets reçus:3018 (2.9 KiB) Octets transmis:7194 (7.0 KiB)


When I run plog the first time, there is nothing but if I run plog after running pon dsl-provider, here are the messages :

Aug 15 16:14:09 localhost pppd[5267]: Plugin rp-pppoe.so loaded.
Aug 15 16:14:09 localhost pppd[5270]: pppd 2.4.4b1 started by root, uid 0
Aug 15 16:14:44 localhost pppd[5270]: Timeout waiting for PADO packets
Aug 15 16:14:44 localhost pppd[5270]: Unable to complete PPPoE Discovery

If I run poff -a and pon dsl-provider, here are the messages :

Aug 15 16:15:38 localhost pppd[5322]: Connect: ppp0 <--> eth0
Aug 15 16:15:41 localhost pppd[5322]: CHAP authentication succeeded: Welcome to use Quidway ROUTER, Huawei Tech.^M^J
Aug 15 16:15:41 localhost pppd[5322]: CHAP authentication succeeded
Aug 15 16:15:41 localhost pppd[5322]: peer from calling number 00:E0:FC:3E:D9:F2 authorized
Aug 15 16:15:41 localhost pppd[5322]: replacing old default route to eth0 [10.0.0.138]
Aug 15 16:15:41 localhost pppd[5322]: Cannot determine ethernet address for proxy ARP
Aug 15 16:15:41 localhost pppd[5322]: local  IP address XX.XX.XX.XX
Aug 15 16:15:41 localhost pppd[5322]: remote IP address XX.XX.XX.XX
Aug 15 16:15:41 localhost pppd[5322]: primary   DNS address XX.XX.XX.XX
Aug 15 16:15:41 localhost pppd[5322]: secondary DNS address XX.XX.XX.XX


Thanks for your suggestions.

---

### Post by bruma on 2006-08-16
I have same problem.

---

### Post by bruma on 2006-08-16
try this [http://www.ubuntuforums.org/showpost.php?p=567725&postcount=12]("http://www.ubuntuforums.org/showpost.php?p=567725&postcount=12")

---

### Post by crobard on 2006-08-19
> **bruma said:**
> try this [http://www.ubuntuforums.org/showpost.php?p=567725&postcount=12]("http://www.ubuntuforums.org/showpost.php?p=567725&postcount=12")

Thanks for the information. It works for me but I had to add the 2 following lines in the file /etc/init.d/bootmisc.sh  :
poff -a
pon dsl-provider

Good luck

---

