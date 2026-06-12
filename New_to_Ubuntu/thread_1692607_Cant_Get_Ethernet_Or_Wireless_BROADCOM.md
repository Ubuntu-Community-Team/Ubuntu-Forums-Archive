---
title: "Cant Get Ethernet Or Wireless BROADCOM"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by lsdirl on 2011-02-21
Hi all 
First off im new to ubuntu I got 10.10 installed on Acer Aspire 3690 laptop and this **** of a broadcom wireless card and to cut a long story short I cant get wireless which from what I see here its not that big of a deal I just need to update and get the firmware so the problem is i cant get ethernet to work either i tried setting the ip and netmask and DNS and its comming up that its connected or active and i can see to arrows up on the top right of the screen and  the lights flashing on the router but if i go to firefox and go to 192.168.1.1 to connect to broadband its unable to connect so i dont know what im missing here is some details any help you would be great and sorry if its a really stupit question and i only need to press a buton or something 
     *-network:0             
         description: Ethernet interface
         product: BCM4401-B0 100Base-TX
         vendor: Broadcom Corporation
         physical id: 1
         bus info: pci@0000:06:01.0
         logical name: eth0
         version: 02
         serial: 00:16:d4:60:96:ff
         size: 100MB/s
         capacity: 100MB/s
         width: 32 bits
         clock: 33MHz
         capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=127.0.0.1 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
         resources: irq:21 memory:d0000000-d0001fff
    *-network:1
         description: Network controller
         product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
         vendor: Broadcom Corporation
         physical id: 2
         bus info: pci@0000:06:02.0
         version: 02
         width: 32 bits
         clock: 33MHz
         capabilities: bus_master
         configuration: driver=b43-pci-bridge latency=64
         resources: irq:22 memory:d0002000-d0003fff
    *-network DISABLED
         description: Wireless interface
         physical id: 2
         logical name: wlan0
         serial: 00:16:cf:b8:ad:35
         capabilities: ethernet physical wireless
         configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg
  0: phy0: Wireless LAN
              Soft blocked: no
              Hard blocked: no
  lo        Interface doesn't support scanning.
   
  eth0      Interface doesn't support scanning.
   
  wlan0     Interface doesn't support scanning : Network is down
   
  auto lo
  iface lo inet loopback

---

### Post by lsdirl on 2011-02-21
ifconfig
  eth0      Link encap:Ethernet  HWaddr 00:16:d4:60:96:ff  
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:21 
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:12 errors:0 dropped:0 overruns:0 frame:0
            TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
            RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

---

### Post by lkraemer on 2011-02-21
There are several HOWTO:'s for Broadcom on the forum..................
One of which is:
[http://ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO%3A+Broadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO%3A+Broadcom)
I know it works, as I've used it on several occasions, and then posted it.

But, I'd suggest searching the forum for the Best HOWTO: and trying the
one that fits your needs.

Post the output of Step #1, disregarding any errors you see, and don't install anything.

What method are you trying to get to work?  B43 Drivers, STA Drivers,
Ndiswrapper?
 
It shouldn't be a big problem.

lk

---

### Post by grahammechanical on 2011-02-21
First of all, look at the listing from ifconfig. Regarding eth0 is says UP and it also says RUNNING. This means that your have a working ethernet connection. so, why are you not connected? It should also say inet addr: And the numbers should be 192.168.1.1, if this is the IP address of your router modem.

Are you plugged in to the modem? Is it switched on? Is the modem connected to the ISP? Network Manager should automatically fetch the correct settings from the router/modem. Go to Edit connections and delete the wired connection that you have set up. You may have put in the wrong settings. Switch the router off and on and see what happens. You may need to do a reboot.

Regards.

P.S. As regards wireless from the first listing you can see that you do have a driver installed, driver=b43 and link=yes. And you are not soft blocked or hard blocked. This is good. If you right click the network manager icon is there a tick mark against Enable Networking and Enable Wireless? If not put one there.

---

### Post by lsdirl on 2011-02-21
[B]Ikraemer i dont know what to i followed your instructions went to this ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO%3A+Broadcom 
and then [/B][B]#2 Use DEFAULT B43 Driver in 10.04 downloaded the files and rebooted and it works thank you so much this was driving me crazy  
[/B]

---

### Post by lsdirl on 2011-02-21
just wondering should i download the B43 driver its telling me too o and thanks again

---

