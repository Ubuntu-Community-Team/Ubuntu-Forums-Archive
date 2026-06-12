---
title: "Cannot create new wireless connection in 8.10 (Intrepid)"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by Arbuz on 2008-11-17
When I go to the Network Manager and try to create a new Wireless Connection, the dialogue "Ok" button is grayed out. I've decided to set the connection up manually, but ran into some trouble.
First of all I want to say that I would like to create an Ad-hoc connection using WEP encryption. I've been researching on that literally for the past 24 hours without any breaks and can't find a solution. :( 
I am using Edimax 7128g PCI Wireless card (RaLink's RT2561/RT61), which is supposed to be recognized by Ubuntu out-of-the-box.
Here's what I get for my wireless when I type lshw -C network:
```
  *-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: wmaster0
       version: 00
       serial: 00:0e:2e:a5:20:d9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11bg
```
By the way, not that I know much about this stuff, but shouldn't "logical name" match my wireless interface? Because ifconfig gives me this:
```
wlan0     Link encap:Ethernet  HWaddr 00:0e:2e:a5:20:d9  
          inet6 addr: fe80::20e:2eff:fea5:20d9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:204 (204.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0E-2E-A5-20-D9-30-64-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
iwlist scan gives me the list of local networks for wlan0, and iwconfig... Well this:
```
wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"default"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=8 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
My question is why can't I create a connection in Network Manager (I've filled up all of the required fields, but "Ok" is still grayed out for some reason). And my attempts to do this manually are also fruitless:
```
~$ sudo iwconfig wlan0 mode ad-hoc
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.
```
Not sure why it is busy by the way. For the past few hours I wasn't even sure if it's even working.
Any clues?

---

### Post by umechanism on 2008-12-27
Did you ever get an answer?  I'm using the same chipset in Intrepid and I can not get the card to activate.  The drivers are installed but the card is dead.  I've tried static, dhcp, command line configurations...basically all the steps that you have posted but I still can not make the card connect.

I'd appreciate any information that you could pass on.

Mike

---

### Post by lazyr on 2009-09-15
The device could be busy because the network manager is using it.
If you right-click on the network manager icon in the notification area, you should be able to enable or disable wireless networking. My guess is that's enabled with you. Disable it and try again.

Comments are highly appreciated!

[edit]
I found this howto in the Wiki: [https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)
[/edit]

---

