---
title: "wlan0 shows disconnected"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by achill3z on 2007-04-21
My wireless card is detected, but it is showing disconnected and I can't enable it...
I installed the drivers for my Dell E1705 Inspiron with the 802.11 Draft n mini wireless card using ndiswrapper. The drivers installed fine, and Edgy recognizes my hardware. I went to System>Administration>Networking and enabled my wireless connection wlan0 and configured it to use DHCP. I have my router, which is a Linksys WRT54GS, set up with WPA-TKIP encryption. I configured wlan0 with the correct passphrase and I entered the correct ESSID . My wifi light on my laptop is lit and if I do a Fn+F2 combination, it turns my wifi light on and off. However, when I go into the wlan0 properties, it shows that the interface is disconnected. Here are the results of several commands that you might find helpful to help me troubleshoot this. One side note/question...do I have to do anything different to enable Edgy to use WPA-TKIP encryption? Or, does it do this natively? One more thing, I have my router set to NOT broadcast my ESSID AND I have MAC address filtering enabled, but, the router lets it on while using Vista, so that shouldn't matter....just want you to know my whole setup.

[HTML]laptop@laptop-laptop:~$ sudo lshw -class Network
Password:
  *-network               
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:a8:ab:47
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.41 firmware=Broadcom,10/12/2006, 4.100.15.5 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:ecffc000-ecffffff iomemory:e0000000-e00fffff irq:177
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:5c:0e:ef
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=full ip=192.168.1.100 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:ecbfe000-ecbfffff irq:177
  *-network
       description: IEEE1394 interface
       physical id: 2
       logical name: eth1
       serial: 34:4f:c0:00:30:53
       capabilities: ieee1394 physical
       configuration: broadcast=yes driver=eth1394 multicast=yes
[/HTML]

[HTML]laptop@laptop-laptop:~$ lspci | grep Broadcom
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)
[/HTML]


[HTML]laptop@laptop-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/HTML]



[HTML]laptop@laptop-laptop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:16:CF:A8:AB:47  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Memory:ecffc000-ed000000 [/HTML]


[HTML]
laptop@laptop-laptop:~$ sudo ifup wlan0
eval: 1: Syntax error: Unterminated quoted string
run-parts: /etc/network/if-pre-up.d/wireless-tools exited with return code 2
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:16:cf:a8:ab:47
Sending on   LPF/wlan0/00:16:cf:a8:ab:47
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/HTML]



[HTML]laptop@laptop-laptop:~$ sudo ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6434
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:16:cf:a8:ab:47
Sending on   LPF/wlan0/00:16:cf:a8:ab:47
Sending on   Socket/fallback[/HTML]

Please Help!

---

### Post by achill3z on 2007-04-22
Just in case there is a question about it, I have disabled all security on my router and my laptop still will not find my network. 

Any ideas?

---

### Post by achill3z on 2007-04-28
Anyone? I'd really like to be able to use Ubuntu wireless

---

### Post by achill3z on 2007-04-29
Is there a command to turn on the wireless card?

---

### Post by achill3z on 2007-05-02
*bump*

---

### Post by ZombiekE on 2007-05-09
I think I had a similar problem. However, upgrading to Edgy and installing some user-made .deb with the firmware for my Broadcom 4318 solved the problem. I have some power issues in Feisty (it's as if the card switched off from time to time and I can only reboot to solve it), but now I can connect wirelessly to the Internet.

---

### Post by achill3z on 2007-06-21
Ok, I'm back to revive my old, dead post. I'm back to square one...I've disabled ALL and EVERY bit of security on my router. I have good results with iwlist. My network now shows up at least. However, I can go into System>Administration>Networking and configure my wifi card, but the status still shows disconnected....PLEASE PLEASE tell me you have some magic words.

---

### Post by Ayuthia on 2007-06-21
Have you tried iwconfig wlan0 essid <essid>?  Once you do that, does it show that it is connected?

---

### Post by linuxonbute on 2007-06-21
Your first post included this :

laptop@laptop-laptop:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:16:CF:A8:AB:47  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Memory:ecffc000-ed000000

which says your card is enabled and working. ( the line:  UP BROADCAST MULTICAST  MTU:1500  Metric:1 )

However this :

aptop@laptop-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

says it is not associated with an access point  ( the line : Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   )

So try  iwconfig wlan0 ap 00:60:1D:01:23:45  ( substitute your access point details )

then see what iwconfig wlan0 says

Note you may have to use sudo   iwconfig wlan0 ap 00:60:1D:01:23:45

---

### Post by achill3z on 2007-06-21
I'm assuming that 00:60:1D:01:23:45 is supposed to be my router's MAC address?

---

### Post by Ayuthia on 2007-06-21
It most likely is your MAC address, but you should be able to find it under Address when you do a 'iwlist scan'.

---

### Post by achill3z on 2007-06-21
Thanks. I'll post results when I get off work this afternoon.

---

### Post by achill3z on 2007-06-22
THANK YOU to everyone who helped me. Thanks to you I'm typing this on my laptop, wirelessly. I followed the how-to on enabling WPA and everything is working good.

---

