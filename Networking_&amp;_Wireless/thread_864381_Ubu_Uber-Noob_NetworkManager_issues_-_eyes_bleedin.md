---
title: "Ubu Uber-Noob NetworkManager issues - eyes bleeding"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by sputnikkk on 2008-07-19
First post - after giving these forums a pretty serious workout for the last few days.  Coming over from the dark side, trying to take the home LAN to linux.  Starting with daughters system. NOT a laptop.

So many things - just DON'T work like Im used to, and getting the software updates and drivers via Synaptic is quite interesting.  I AM learning a bunch and still trying. CompizFusion - what a trip that was/is.

Ok so ... 
Ubuntu 8.04 Hardy
RaLink rt2500pci drivers 
Card is a Linksys WMP54G
Static IP - 192.168.1.18 on the the desktop in question
Router is a linksys WRT310N Gigabit Wired/Wireless b/g/N
Trying to run WAP2


wlan0     Link encap:Ethernet  HWaddr 00:12:17:86:53:6b  
          inet addr:192.168.1.18  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe86:536b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44985 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43625 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6527110 (6.2 MB)  TX bytes:14967186 (14.2 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-12-17-86-53-6B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Scan completed :
          Cell 01 - Address: 
                    ESSID:"myESS_ID"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/100  Signal level=-51 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

*-network               
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: d
       bus info: pci@0000:02:0d.0
       logical name: wmaster0
       version: 01
       serial: 00:12:17:86:53:6b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.1.18 latency=32 module=rt2500pci multicast=yes wireless=IEEE 802.11g

                    
Ok so after all that wonderful information - the issues are that after every reboot/update, I have to go into the NetworkManager GUI and change the security level from WPA to WPA2, and re enter the passphrase/code. 

Why doesnt it save these settings?  Whats causing them to change?  I saved a location profile as well.  Is there a fix for this?

---

### Post by chili555 on 2008-07-19
> NOT a laptop.Then you don't really need Network Manager. I suggest disabling Roaming and configuring your WPA details as suggested here: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

Once you have it working, go into Synaptic and remove Network Manager and his little henchman dhcdbd. It will then connect on boot with no human intervention.

---

### Post by sputnikkk on 2008-07-19
Thank you Chili !

I have seen that thread and read it many times but ... I was troubled by.

> 6. RTxxx (Ralink) drivers do not support this approach. Either install "ndiswrapper" replacing Serialmonkey's driver or visit this site.

I have a Ralink chipset card using driver rt2500pci

---

