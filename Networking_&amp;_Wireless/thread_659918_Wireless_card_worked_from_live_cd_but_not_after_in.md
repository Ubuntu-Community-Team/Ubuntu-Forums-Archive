---
title: "Wireless card worked from live cd but not after install"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by jonneyboimc on 2008-01-06
hi firstly im a noob, so i wasn't sure were to post this but neways.. As it says in the title i cant get my network card to work it is a prism card in a fujitsu siemans amilo pro v7010. when you click on the network icon in the top right it has wireless networks then noting. i dont kow wether ubuntu has even reconised my card.. pls help many thanks jonney

---

### Post by (((X))) on 2008-01-06
press wifibutton, maybe its just off. 
could you post here output of iwconfig (works like ipconfig in windows)

---

### Post by jonneyboimc on 2008-01-06
hi,, i tryed pressing Fn then the button with the wifi and the laptop froze and two lights buy the power lights started flashing.. thease are the results for the thing u told me to do. :). thanks 

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      NOT READY!  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=31 dBm   Sensitivity=0/200  
          Retry short limit:0   RTS thr=0 B   Fragment thr=0 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by (((X))) on 2008-01-06
Interface for your wificard is a there, try restricted drivers manager, its improved in gutsy..I got my wifi working without ndiswrappers.

---

### Post by jonneyboimc on 2008-01-06
hmm the only thing in restricted drivers is software modem drive and this is enabled with it status as in use..:confused:

---

### Post by (((X))) on 2008-01-06
are you able to connect wirelessly
code:
ifconfig

---

### Post by jonneyboimc on 2008-01-06
Not to sure what you mean but i cant even view my wireless network, which is working fine as my phone is connected. when i try ipconfig this is what i get: btw im using a wired connection to connect to the internet at the moment:: 

jonney@JoNNeYs-Lappy:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:73:7F:7A  
          inet addr:86.0.75.183  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::2c0:9fff:fe73:7f7a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12076 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15037069 (14.3 MB)  TX bytes:1200946 (1.1 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by (((X))) on 2008-01-06
you have to install drivers for it...
code:
lspci 
this will show all pcihardware, this way you see exactly that wlancard you have, google for drivers, manals to get it to work..

---

### Post by jonneyboimc on 2008-01-06
Arrrrrrhhh lol why is linux so difficult.. This is what i get.

02:02.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

What bits of infromation do i need to google.. sorry mate abount this..

---

### Post by rustybronco on 2008-01-06
Linux difficult? it's just that you are not use to it yet. I just put in a new hard drive reset up my whole system in about 1-1/2 hours from scratch ( no backup disk ) updates and all plus all my "favorite add ons".
Back to your problem, did you get to go online wireless with the live cd or no? 
what you need to search for are posts on " ISL3886 " such as this one [http://ubuntuforums.org/showthread.php?t=600309](http://ubuntuforums.org/showthread.php?t=600309) or this one [http://lists.debian.org/debian-laptop/2004/11/msg00191.html](http://lists.debian.org/debian-laptop/2004/11/msg00191.html)

No need to be sorry, glad to try and help.

---

### Post by jonneyboimc on 2008-01-06
Yes.. thats whats confusing me if i use the live cd it like automatically finds the wirelss network no configuration or any thing all i had to do was enter the wep key.. anyway ill try thoes posts u suggested :)

---

### Post by rustybronco on 2008-01-06
> **jonneyboimc said:**
>  if i use the live cd it like automatically finds the wirelss network no configuration or any thing all i had to do was enter the wep key..  and you can go online with wireless correct?

see this post [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188) about connecting from the command line which is part of the link in my signature.

---

