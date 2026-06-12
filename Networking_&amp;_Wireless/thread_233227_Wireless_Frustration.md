---
title: "Wireless Frustration"
date: 2006-08-09
forum: Networking &amp; Wireless
---

### Post by aclipse3425 on 2006-08-09
I've got a notebook with integrated wifi-b and its up and running.. I just can't get it to connect to my Access Point

Here's the info I've gathered
Some things to note-- the Frequency is not the one my AP is set to nor is the AP MAC address mine.. Its obviously someone else's in my vicinity..  

atchang@washu:~$ iwconfig eth1
eth1      IEEE 802.11b  ESSID:"btchangwifi"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:3D:5D:29:88
          Bit Rate:2 Mb/s   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=-68 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0

atchang@washu:~$ iwconfig eth1
eth1      IEEE 802.11b  ESSID:"btchangwifi"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:3D:5D:29:88
          Bit Rate:2 Mb/s   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=-68 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0


atchang@washu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid btchangwifi
wireless-mode managed
wireless-channel 11
wireless-key FFFFFFFFFFFFFFFF  

Any help is appreciated !!!

-- aclipse

---

### Post by wieman01 on 2006-08-09
A few questions:

1. Your settings tell me you want to use WEP wireless security.
2. You connect to the router through DHCP.
3. You connect through channel 11.

If any of these statements are wrong, then it's no surprise you cannot connect. :-)

I would remove those two lines so as to enable the wireless card's auto-function:
> wireless-mode managed
wireless-channel 11
Apart from this the settings look just fine.

---

### Post by aclipse3425 on 2006-08-09
Thanks for your response..
answers to questions
1-3 are all yes..

But I've removed to two lines as you suggested...

I get the same results.. It appears to connect to some other nearby unsecured node and still doesn't successfully acquire an address via DHCP.. not that I would know whether DHCP is available on some strange access point.  

BTW:Is it possible there are setting stored elsewhere beside /etc/network/interfaces ?


-- aclipse

---

### Post by wieman01 on 2006-08-10
"/etc/network/interfaces" is pretty much the only place where network related information is stored (with one exception which we can ignore at this point... /etc/resolv.conf).

Can you rename your network's essid/name? It's unlikely but perhaps your neighbor's network has got the same essid???

---

