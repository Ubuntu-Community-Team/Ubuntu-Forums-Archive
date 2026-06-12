---
title: "can't connect to usual connection after installing Ibis"
date: 2008-11-29
forum: Networking &amp; Wireless
---

### Post by carboncopied on 2008-11-29
I upgraded to Ibis a few days ago and right away had trouble connecting to my usual connection (WPA2 personal protected wireless apple router)

I can connect to a non-protected wireless on another router, but can't seem to connect when I give it WAP protection.

I suspect that the problem is with the network manager as everything worked before the upgrade and when I keep playing with the network manager it ends being weird and I have to unplug the usb card.

details:

Linksys compact Wireless-G USB adapter

$ lsusb:
Bus 003 Device 003: ID 13b1:0020 Linksys WUSB54GC 802.11g Adapter [ralink rt73]

ifconfig:
wlan0     Link encap:Ethernet  HWaddr 00:18:39:12:fd:3f  
          UP BROADCAST MULTICAST  MTU:576  Metric:1
          RX packets:196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:239 errors:0 dropped:18 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34614 (34.6 KB)  TX bytes:36150 (36.1 KB)

iwconfig just before it gives up, on original network

wlan0     IEEE 802.11g  ESSID:"Air Jordan"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1E:52:7A:30:E5   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwconfig shortly after

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Auto  Frequency:2.452 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ lsmod:
usbcore               148848  9 snd_usb_audio,snd_usb_lib,ndiswrapper,gspca_spca508,gspca_main,usbhid,ohci_hcd,ehci_hcd


$ sudo lshw -C network:
  *-network:0             
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:39:12:fd:3f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt73 driverversion=1.53+Linksys, A Division of Cisc link=no multicast=yes wireless=IEEE 802.11g

Ubuntu 8.10

2.6.27-9-generic i686


If you got this far, thanks for reading.

---

### Post by cmnorton on 2008-11-29
Are you running Network Manager and getting DHCP from any one of these routers?

You may have to re-establish the encrypted connection by connecting to the wireless network as if you have never connected before. When prompted for your encrypted string in Network Manager, make sure you pick the setting that matches the string.

I keep my encrypted string in hex form, so I choose that setting, rather than the original string that was translated into hex.

---

### Post by carboncopied on 2008-11-29
how can I tell if I'm getting DHCP?

I have tried manually entering all the details for each connection. It was effective once, but hasn't worked since.

---

### Post by J172 on 2008-11-29
You can go to System->Preferences->Network and click your Interface, click edit. Go to the IPv4 Tab and see if its on DHCP (Automatic).

---

### Post by carboncopied on 2008-12-01
it is on DHCP (automatic)

---

### Post by carboncopied on 2008-12-01
I reloaded my drivers and now I can't connect with any wireless. 

it goes through all the motions, but just doesn't finish the connection.

---

### Post by praerien on 2009-01-06
I have just upgraded to ibis. Afterwards, I couldn't connect to my wireless router using WPA2. The problem went away after I turned the router off and on :D

---

