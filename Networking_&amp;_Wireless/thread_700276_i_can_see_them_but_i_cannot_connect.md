---
title: "i can see them but i cannot connect"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by littletinman on 2008-02-18
My wireless is working i guess, but now it won't connect. it just says connecting for about 15 seconds then goes back to the wicd thing. I have an acer aspire 5520. I really really need help. can someone help me figure out why it's not getting the ip address?

---

### Post by Hightide on 2008-02-18
Hi


can you post output from

```
sudo ifconfig
```

regards

:)

---

### Post by littletinman on 2008-02-18
output is this;
eth16     Link encap:Ethernet  HWaddr 00:00:6C:07:E1:7E  
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::200:6cff:fe07:e17e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:601 errors:0 dropped:0 overruns:0 frame:0
          TX packets:489 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:538102 (525.4 KB)  TX bytes:74257 (72.5 KB)
          Interrupt:20 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Memory:f2200000-f2210000

---

### Post by Hightide on 2008-02-18
HI Littletinman

wlan0 Link encap:Ethernet HWaddr 00:00:00:00:00:00 

This indicates no router association and  you have no assigned IP address.

as i have to rush off have a look at the Ubuntu [wiki ]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")particularly on the Router section


regards

:)

---

### Post by ajdebemiren on 2008-02-18
What kind of connection you are trying to make !!! Post information from "iwconfig wlan0"

---

### Post by littletinman on 2008-02-18
wlan0     IEEE 802.11g  ESSID:"Royer Family Network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Here's the config thing ajdebemiren wanted. What kind of connection do i want to make. I'm a newbie when it comes to wifi.

---

### Post by ajdebemiren on 2008-02-18
On what kind of network you are trying to connect !!! It is Ad-Hoc or AP ???????

---

### Post by littletinman on 2008-02-18
Whats the difference. It's a private network. What is adhok or ap? how can i tell. I'm not all wifi savvvy

---

### Post by anidritesolforosa on 2008-02-18
Have you got a router??? If yes you have to configure your router. If it is configured try to boot without dongle and insert it after the login screen. This is what it happened to me after upgrading from Dapper 6.06. The system installs other devices like avahi and wlan0 and it won't connect but as a temporary fix that is what I need to do to get the network going. Hope it helps

---

### Post by littletinman on 2008-02-18
well the netowrk is running from a dif computer. I don't really understand what i'm uspposed to do. What is a dongle?

---

### Post by nsimeone2000 on 2008-02-18
This may sound stupid, but it worked for me, so hopefully it will work for you.

If restart your computer, you won't have a light, but, if you go to system, administration, then network you will see your wired connection, your wireless connection and the modem one......

If you go ahead and click the check box next to wired, it will disconnect your wireless completely and say that it is configuring, after that is complete then uncheck it, and your wireless will identify the networks again, you should be able to connect to one at that point in time.

What type of network are you trying to connect to?  Mine was a WEP, so I just turned it off, so there is no security and it works like a charm everytime I load up Ubuntu.

I totally understand your frustration though.

---

### Post by littletinman on 2008-02-19
Mines either WEP or WAP i don't have my lappy booted up right now to see but i'll let you know. I'll try what you said. Thanks so much for your patience.

---

### Post by anidritesolforosa on 2008-02-19
The dongle is the stick that you plug in the usb port, basically is a network card as it were but you did not answer my question: have you got a router???

---

### Post by littletinman on 2008-02-19
My wifi is built into my computer. There is a router. I can see it but it won't get the ip address from it. Do i have to do this manually? It worked for 3 hours on saturday then all of the sudden i couldn't connect. I'm using WEP and wicd. Not network manager.

 Help please.

---

### Post by anidritesolforosa on 2008-02-19
from the output of your ipconfig the wlan0 has no hardware address 00000000 I do not know what that means (hardware fault?) but it does not look good. Also it seems that you have an active ethernet wired card in your system try to disable it (from the bios) Either my network is functioning or not I always get an hardware address for my card. This is the output of my ifconfig 
ifconfig output no network
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:112 (112.0 b)  TX bytes:112 (112.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:FB:AE:C3
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0:ava Link encap:Ethernet  HWaddr00:11:50:FB:AE:C3
          inet addr:169.254.9.70  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-00-11-50-FB-AE-C3-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

and this is when is working i.e. when I insert the stick after the login screen (modem and router must be already on)

ifconfig output network ok!
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:FB:AE:C3
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:febf:8ed3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:648 (648.0 b)  TX bytes:572 (572.0 b)

---

### Post by littletinman on 2008-02-19
hmmmm. wel ii use my ethernet too. I don't want to dissable it from the bios. I wonder if i have the wrong driver for my card.

---

### Post by anidritesolforosa on 2008-02-19
can you ping your router? Try also iwconfig and see if you get the hardware address for it. If it says "Not Associated" you will never get an IP address assigned to your card by the router(assuming that the router is also a DHCP server). Other useful commands to run in your teminal are 
ifconfig
iwconfig
lspci | grep Ethernet
sudo iwlist scan
they may help you to determine what is going on. Hope you will crack it!

---

### Post by littletinman on 2008-02-19
how do i ping my router? There's an option for it in "Network Tools" but i think i need an adress.

---

### Post by Hidetsu on 2008-02-19
i'm having the same problem
got Wlan0 installed and got my RT73.ko installed but I can't connect :(

when i do "iwconfig wlan0"

user@user-desktop:-$ iwconfig wlan0
wlan0   RT73WLAN     ESSID: " "
            Mode: Managed    Frquency=2.412   GHz    Bit rate=54Mb/s
            RTS thr:off          Fragment thr:off
            Link Quality=0/100    Signal level:-121  dBm    Noise level:-11 dBm
            Rx invalid nwid:0   Rx invalid crypt:0    Missed beacon:0


I'm using a DWL-G122 D-link Ver.:C1
with a ubuntu 6.06 dapper

My router is a D-link AirPlus Xtreme G

Thanks

---

### Post by nsimeone2000 on 2008-02-20
Alright, well the network manager kind of sucks, try this out and see if this works for you
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

