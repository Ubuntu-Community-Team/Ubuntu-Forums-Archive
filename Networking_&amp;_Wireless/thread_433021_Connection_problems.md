---
title: "Connection problems"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by bramarama on 2007-05-04
hi all,

i am testing ubuntu 7.04 at the moment.
This OS really were a big suprice for me, i only used windows 98, NT/2000 and XP bevor.
(so i am a newbie in Linux and dont know to help me by myself)
There were no problems installing ubuntu, it looks nice and its really easy to update.
Only one thing is really anoing me.

After starting my pc i can connect to internet, it runs as fast as it should..

When i try to connect to internet some hours (dont exactly know how long the pc have to be disconnected) there is no way to get connection.

I am using an onboard ethernet-controller (board asus m2n-e) and an old telekom-dsl-router.

I am using 192.168.1.61 for static ip-adress, router is using 192.168.1.1, both with subnetmask 255.255.255.0. (i believe this is an configuration a lot of people uses)

When the connection disconnectet i am not able to ping the router, all packages misses.

If i try to change ip adress or something else, my pc dont get connection again, only a reboot is working,
After i reboot the pc all is running fine as long as i use any internetconnection without disruption, but when i leave for some time the same problem is there again.

I hope anyone can understand me (i am german) and knows to help me.

greetings

edit:

other PCs are using the same router to connect to the internet.
I tried to connect to the internet with one of this other PCs and its working fine (with windows...)
so i think the reason have to be my pc/the ubuntu

---

### Post by Blacktalon on 2007-05-04
hmm...There might be something that isn't set up right on your mechine.

But you can try this trick:
  Application==>Terminal (click)==>

(type) sudo dhclient3 (hit enter button)

This will take a moment to go through, but it should resablish a connect.  A faster is if you know what your Card is called, i.e. : eth1(this is what most wireless cards are called)  Then you can just do:  sudo dhclient3 eth1( or whatever it is called).  That will try re-establish an address with the router in a few seconds.

Another possiblity is that you are using a non-generic type card, in which case you would need to do a little research on how to get it up and running.  Most of that can be found at the Ubuntu Wiki for drivers and suchs.

I would suggest reading over [WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")
And 

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#")

I hope this helps,
~BT

---

### Post by bramarama on 2007-05-05
> **Blacktalon said:**
> hmm...There might be something that isn't set up right on your mechine.

But you can try this trick:
  Application==>Terminal (click)==>

(type) sudo dhclient3 (hit enter button)

This will take a moment to go through, but it should resablish a connect.  A faster is if you know what your Card is called, i.e. : eth1(this is what most wireless cards are called)  Then you can just do:  sudo dhclient3 eth1( or whatever it is called).  That will try re-establish an address with the router in a few seconds.

Another possiblity is that you are using a non-generic type card, in which case you would need to do a little research on how to get it up and running.  Most of that can be found at the Ubuntu Wiki for drivers and suchs.

I would suggest reading over [WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")
And 

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#")

I hope this helps,
~BT

well i testet "(type) sudo dhclient3 (hit enter button)" but as I thought it doesnt work.
If I understand this command right, it should get a new ip from dhcp.
The problem is, my router (teledat530) isnt the dhcp in my network, every pc got an own static ip.
I configured all pc in my network to use the router for gateway.

I dont know what a non generic ethernetcontroller is, but the controller is working fine after every reboot. 

by the way my ethernetcontroller is called eth0, ifconfig says:

eth0      Protokoll:Ethernet  Hardware Adresse 00:18:F3:B7:C6:FD  
          inet Adresse:192.168.1.61  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6 Adresse: fe80::218:f3ff:feb7:c6fd/64 Gültigkeitsbereich:Verbindung


greetings

---

