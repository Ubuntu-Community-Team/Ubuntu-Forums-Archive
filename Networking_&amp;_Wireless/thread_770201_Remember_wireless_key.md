---
title: "Remember wireless key"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by okey666 on 2008-04-27
Ok, hopefully this should be simple to sort out. I am using a wireless network with an Orange Livebox router and a 8.04 upgrade from gutsy. On my 7.10 gutsy install before I upgraded the network manager used to remember my wireless key, but now it forgets it and I have to enter it every time. 

Does anyone know how to get the key-ring to remember my key?

---

### Post by okey666 on 2008-08-07
Anyone? I can practically remember my 26 digit key by now!

---

### Post by dasunst3r on 2008-08-07
What's sad is that I can remember my 26-digit key as well, and I don't have to enter it quite as often.  Mind you, I've had four years to memorize mine instead of a couple days, but I digress.  Try right-clicking on your NetworkManager applet icon and clicking "Edit Wireless Networks."  If there is anything wrong in the profile you're using, change it.

---

### Post by chili555 on 2008-08-07
Are these laptops that roam down to the coffee shop that would benefit from being able to manage an ever-changing environment? Or are these stay-at-home computers that don't really need Network Manager and for whom these details could, once and for all, be placed in */etc/network/interfaces*?

---

### Post by okey666 on 2008-08-07
ok, nice to have a response.

I have tried editing the network using "edit network" before. Usually, it totally drops the connection then and needs the network to be deleted. The key that was displayed there, was, as usual, totally wrong. I have replaced it with the correct one and (as of yet (2 mins)) the connection has not been dropped and a key required.

> Or are these stay-at-home computers that don't really need Network Manager and for whom these details could, once and for all, be placed in /etc/network/interfaces? 
I am using a desktop, so yes I could do that. Do you know where I could find a How to on it (I have tried before. Or could you guide me through the process?

---

### Post by okey666 on 2008-08-07
Well, a few minutes later, my connection was dropped. Strange how it goes from 21% to no connection in a matter of seconds. BUT, it did remember the key, which it sometimes does anyway. We will see if it can remember it again...

---

### Post by chili555 on 2008-08-07
> I am using a desktop, so yes I could do that. Do you know where I could find a How to on it (I have tried before. Or could you guide me through the process?Here is a great tutorial: [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by okey666 on 2008-08-07
Ok... Even though I edited the key, the network was once again forgotten and the key was reset to the strange long number.

Ok... I did this to try and set up a WEP connection (my router is set to WEP or WPA)
> oscar@oscar-desktop:~$ iwconfig ath0
ath0      IEEE 802.11g  ESSID:"KEY-WIRE-LESS_SYSTEM"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:4442  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

oscar@oscar-desktop:~$ sudo iwconfig ath0 key s:ASCII_KEY 00000000000D00000000000000 (0=number D=letter if thats any help)
oscar@oscar-desktop:~$ sudo iwconfig ath0 key open
oscar@oscar-desktop:~$ sudo iwconfig ath0 mode Managed
oscar@oscar-desktop:~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:18:4d:ed:94:8b
Sending on   LPF/ath0/00:18:4d:ed:94:8b
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


I followed the how-to given which I have tried to use for WPA before and failed. When I tried for WEP, that is what happened. Anyone give me a point in the right direction.

---

### Post by okey666 on 2008-08-07
As I am using MadWifi, this could help me:
[http://ubuntuforums.org/showthread.php?t=540101](http://ubuntuforums.org/showthread.php?t=540101)

---

