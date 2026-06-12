---
title: "Problem with wifi connection"
date: 2014-10-25
forum: Networking &amp; Wireless
---

### Post by paul.zierep on 2014-10-25
Hi Ubuntu users, I am very new to Ubuntu, so my knowledge of the commands is limited :) I have the following problem, I use ubuntu 14.04 LTS, the computer is: Lenovo B590, my wifi driver configs are:

   02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
     Subsystem: Lenovo Device [17aa:0611]

     Kernel driver in use: bcma-pci-bridge
 03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)

     Subsystem: Lenovo Device [17aa:5002]
     Kernel driver in use: r8169

For some reasons my wifi just stops sometimes and ubuntu can´t reconnect... which means that I have to reboot the rooter, which is quiet a problem as there are a lot of other people who live here :) After rebooting it usually works again, but eventually stops at some point. 

Any help on this one ? I provide any further information needed, just tell me which commands to use. 
Thank you guys !!

---

### Post by Bucky Ball on 2014-10-25
Welcome. Please open a terminal and paste this in:

```
sudo lshw -C network
```

Post the output back here.

---

### Post by paul.zierep on 2014-10-25
*-network               
       Beschreibung: Kabellose Verbindung
       Produkt: BCM43142 802.11b/g/n
       Hersteller: Broadcom Corporation
       Physische ID: 0
       Bus-Informationen: pci@0000:02:00.0
       Logischer Name: wlan0
       Version: 01
       Seriennummer: 1c:3e:84:e7:b5:c3
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress bus_master cap_list ethernet physical wireless
       Konfiguration: broadcast=yes driver=wl0 driverversion=6.30.223.141 (r415941) ip=192.168.1.224 latency=0 multicast=yes wireless=IEEE 802.11abg
       Ressourcen: irq:17 memory:90500000-90507fff
  *-network
       Beschreibung: Ethernet interface
       Produkt: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       Hersteller: Realtek Semiconductor Co., Ltd.
       Physische ID: 0
       Bus-Informationen: pci@0000:03:00.0
       Logischer Name: eth0
       Version: 07
       Seriennummer: 3c:97:0e:bf:d6:51
       Größe: 10Mbit/s
       Kapazität: 1Gbit/s
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       Konfiguration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       Ressourcen: irq:41 ioport:2000(Größe=256) memory:90404000-90404fff memory:90400000-90403fff

---

### Post by paul.zierep on 2014-10-25
Sorry my fault, where do I set the terminal in english ?

---

### Post by paul.zierep on 2014-10-25
Alright here it is: 
  *-network               
       description: Wireless interface
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 1c:3e:84:e7:b5:c3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.141 (r415941) ip=192.168.1.224 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:90500000-90507fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 07
       serial: 3c:97:0e:bf:d6:51
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:2000(size=256) memory:90404000-90404fff memory:90400000-90403fff

---

### Post by Rob Sayer on 2014-10-25
Here's a guide to what driver you should be using, read carefully:

[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

---

### Post by Bucky Ball on 2014-10-25
The wl is the driver this card should be using and it's there. Much simpler, and if you want to make absolutely sure that it is installed correctly, is [THIS]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29_-_12.10_.28Quantal_Quetzal.29") link. Couple of lines of code. Should work fine for 14.04.

---

### Post by paul.zierep on 2014-10-25
Thank you two, but I´ve already done that before.

```
paul@paul-Lenovo:~$ sudo apt-get update
[sudo] password for paul: 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty InRelease
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports InRelease                    
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty Release.gpg                           
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates Release.gpg                   
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports Release.gpg                 
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty Release                               
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates Release                       
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports Release                     
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/main Sources                          
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/restricted Sources                    
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/universe Sources                      
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/multiverse Sources                    
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/main amd64 Packages                   
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/restricted amd64 Packages             
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/universe amd64 Packages               
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/multiverse amd64 Packages             
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/main i386 Packages                    
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/restricted i386 Packages              
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/universe i386 Packages                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/multiverse i386 Packages              
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/main Translation-de                   
OK   [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                           
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/main Translation-en                   
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/multiverse Translation-de             
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/multiverse Translation-en             
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/restricted Translation-de             
OK   [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                    
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/restricted Translation-en             
OK   [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                               
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/universe Translation-de               
OK   [http://archive.canonical.com](http://archive.canonical.com) trusty Release                               
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/universe Translation-en               
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/main Sources                  
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/restricted Sources            
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/universe Sources              
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/multiverse Sources            
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/main amd64 Packages           
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/restricted amd64 Packages     
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/universe amd64 Packages       
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages     
OK   [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                        
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/main i386 Packages            
OK   [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                   
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/restricted i386 Packages      
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/universe i386 Packages        
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/multiverse i386 Packages      
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/main Translation-en           
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/multiverse Translation-en     
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/restricted Translation-en     
OK   [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                   
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/universe Translation-en       
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/main Sources                
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/restricted Sources          
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/universe Sources            
OK   [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                              
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/multiverse Sources          
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/main amd64 Packages         
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/restricted amd64 Packages   
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/universe amd64 Packages     
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages   
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/main i386 Packages          
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/restricted i386 Packages    
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/universe i386 Packages      
OK   [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources             
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/multiverse i386 Packages    
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/main Translation-en         
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/multiverse Translation-en   
OK   [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                       
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/restricted Translation-en   
OK   [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/universe Translation-en     
OK   [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources               
OK   [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                        
OK   [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources             
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/main Translation-de_DE                 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/multiverse Translation-de_DE           
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/restricted Translation-de_DE           
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/universe Translation-de_DE             
OK   [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages            
OK   [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages      
OK   [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages        
OK   [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages      
OK   [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                       
OK   [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages             
OK   [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                
OK   [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages       
OK   [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                 
OK   [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages         
OK   [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                
OK   [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages       
OK   [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en    
OK   [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en      
OK   [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-de_DE                     
OK   [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-de                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Paketlisten werden gelesen... Fertig     
```

                                      
paul@paul-Lenovo:~$ sudo apt-get install bcmwl-kernel-source
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
bcmwl-kernel-source ist schon die neueste Version.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiertAs you can see I am using the STA driver (wl), thats how I made the wifi run in first place...already took a while to figure that out :) 
So the problem is not the driver I guess, but rather some problem with the connection...

Anyway I found this:
[http://askubuntu.com/questions/457729/ubuntu-14-04-wireless-constantly-disconnects](http://askubuntu.com/questions/457729/ubuntu-14-04-wireless-constantly-disconnects)

modprobe -r iwlwifi && modprobe iwlwifi 11n_disable=1
sudo iwconfig wlan0 power off

Tryed it and it seems to work fine at the moment, already connected for about 3h...if anybody could explain what I actually did, I would
very much appreciate it. 

But thank you two very much for the quick response, I am very impressed with this forum !!

---

### Post by Hexxus on 2014-10-25
Quick question, does it work perfectly if you only reboot the laptop and leave the router alone?

I've got a similar problem with an older WLAN card however it doesn't support N. It might help us identify something.

---

### Post by paul.zierep on 2014-10-25
Hi Hexxus, no, ones the wifi does not connect anymore it won´t chance when I reboot ...it stays disconnected. Only a reboot of the rooter solved the problem so far for about 20 min....but as I said with the last changes its working, but I don´t actually know what I did there :) Hope that helps. Its midnight in australia, so hear from you tomorrow maybe...

---

### Post by Bucky Ball on 2014-10-25
@paul.zierep: Please use [code] tags for code. Neater, space saving and much easier to read. See the last link in my signature for how. Thanks. ;)

I've done one for you as an example. :-k

---

### Post by paul.zierep on 2014-10-26
@ Bucky Ball: Thank you very much I was already looking for that. I´ll do so in the future. 

As for my problem it is still happening, seems to me I was just lucky yesterday... when I started the computer this morning it could not connect to the wifi. Only rebooting the rooter solved the problem for the moment, but I mean this can´t be the solution for ever :) 

Any Ideas ? I mean it shows me the wifi network, but it just does not connect to it ...

---

### Post by paul.zierep on 2014-10-26
Nobody got an idea ? I mean there must be some more things to do, no ?

---

### Post by Bucky Ball on 2014-10-26
Follow the steps [HERE]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29_-_12.10_.28Quantal_Quetzal.29"). You mention you have, though. If that doesn't work, I'm a bit stumped. Not a wireless guru, but this might bump the thread and draw the attention of one.

Have you tried deleting your wireless connection in Network Manager, rebooting and seeing if it lets you know of available networks? Connect to yours and see what happens. If it drops, before doing anything else, open a terminal and paste in:

```
dmesg
```

Post back the lines at the end which describe what happened to wireless. 

Are others connecting to this router without issue?

---

### Post by JeQhdMD on 2014-10-26
Another approach to wifi connectivity is simply to get a proven usb wifi adapter such as the TP-Link "TL-WN722N" or the Panda Ultra WiFi b/g/n.   Each are plug & play on my Lenovo h410 running several buntu's 12.04==>14.04.   The 722 seems to have better range, although the Panda does just fine.  The Airlink 101 AWLL 5088 also works great.   The panda and airlink are micro-dongles (great for laptops), and the TP-Link is like a standard USB stick with an antenna.   Cost for these ranges from about 10.00 to 24. usd. via Amazon.  Have had "zero" dropped connections in about 30 months on several devices, average download about 40MbS, 5 upload.

Tschuss

---

### Post by paul.zierep on 2014-10-27
@Bucky Ball: I'll do so when I get home from work, let's see what happens.
@JeQhdMD: Thank you for the idea, I think about getting an adapter. But I mean if it drops just like this and then can't reconnect but can reconnect after rebooting the rooter (signal is the same and the wifi is shown as a available network all the time ), this does not seem to be a problem related to connectivity...?

---

### Post by Bucky Ball on 2014-10-27
No, it doesn't. Your wireless card seems to be up and running fine, is known to work with Ubuntu and has the correct driver installed by the looks. Wouldn't consider purchasing a dongle just yet. I'm curious about the router, though, which is why I ask if others are connected to it fine or if you can connect any other machines or Win without issue. :-k

Have you tried running it on another channel? Perhaps get into the router config and have a look around (router IP in a browser). There could be an odd setting somewhere. What security are you using (WPA2, WEP?)? And change the channel to 1 if it isn't there already.

---

### Post by paul.zierep on 2014-10-27
So I did start my computer just now and it did not connect to  the Wifi, after dmesg I get this: 

```

1
[    0.862099] usb usb1: Product: EHCI Host Controller
[    0.862100] usb usb1: Manufacturer: Linux 3.13.0-37-generic ehci_hcd
[    0.862102] usb usb1: SerialNumber: 0000:00:1a.0
[    0.862215] hub 1-0:1.0: USB hub found
[    0.862222] hub 1-0:1.0: 3 ports detected
[    0.862405] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.862409] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.862421] ehci-pci 0000:00:1d.0: debug port 2
[    0.866323] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.866339] ehci-pci 0000:00:1d.0: irq 23, io mem 0x90619000
[    0.878059] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.878093] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.878095] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.878096] usb usb2: Product: EHCI Host Controller
[    0.878098] usb usb2: Manufacturer: Linux 3.13.0-37-generic ehci_hcd
[    0.878099] usb usb2: SerialNumber: 0000:00:1d.0
[    0.878229] hub 2-0:1.0: USB hub found
[    0.878237] hub 2-0:1.0: 3 ports detected
[    0.878347] ehci-platform: EHCI generic platform driver
[    0.878356] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.878357] ohci-pci: OHCI PCI platform driver
[    0.878365] ohci-platform: OHCI generic platform driver
[    0.878369] uhci_hcd: USB Universal Host Controller Interface driver
[    0.878468] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.878472] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.878568] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.878592] xhci_hcd 0000:00:14.0: irq 40 for MSI/MSI-X
[    0.878652] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.878653] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.878655] usb usb3: Product: xHCI Host Controller
[    0.878656] usb usb3: Manufacturer: Linux 3.13.0-37-generic xhci_hcd
[    0.878658] usb usb3: SerialNumber: 0000:00:14.0
[    0.878795] hub 3-0:1.0: USB hub found
[    0.878809] hub 3-0:1.0: 4 ports detected
[    0.879120] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.879123] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.879155] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.879156] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.879158] usb usb4: Product: xHCI Host Controller
[    0.879159] usb usb4: Manufacturer: Linux 3.13.0-37-generic xhci_hcd
[    0.879160] usb usb4: SerialNumber: 0000:00:14.0
[    0.879303] hub 4-0:1.0: USB hub found
[    0.879316] hub 4-0:1.0: 4 ports detected
[    0.886210] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.889440] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.889446] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.889618] mousedev: PS/2 mouse device common for all mice
[    0.889826] rtc_cmos 00:06: RTC can wake from S4
[    0.889939] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.889967] rtc_cmos 00:06: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.890019] device-mapper: uevent: version 1.0.3
[    0.890088] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.890095] ledtrig-cpu: registered to indicate activity on CPUs
[    0.890181] TCP: cubic registered
[    0.890250] NET: Registered protocol family 10
[    0.890397] NET: Registered protocol family 17
[    0.890406] Key type dns_resolver registered
[    0.890631] Loading compiled-in X.509 certificates
[    0.891468] Loaded X.509 cert 'Magrathea: Glacier signing key: 2cb1133b35f95a9e24deabeeb12ba449bcbabbc9'
[    0.891479] registered taskstats version 1
[    0.893322] Key type trusted registered
[    0.894899] Key type encrypted registered
[    0.896384] AppArmor: AppArmor sha1 policy hashing enabled
[    0.896387] IMA: No TPM chip found, activating TPM-bypass!
[    0.896669] regulator-dummy: disabling
[    0.896720]   Magic number: 2:818:37
[    0.896731] bdi 7:2: hash matches
[    0.896808] rtc_cmos 00:06: setting system clock to 2014-10-27 17:01:02 UTC (1414429262)
[    0.897117] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.897119] EDD information not available.
[    0.897158] PM: Hibernation image not present or could not be loaded.
[    0.897940] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    0.897941] Write protecting the kernel read-only data: 12288k
[    0.899853] Freeing unused kernel memory: 804K (ffff880001737000 - ffff880001800000)
[    0.901520] Freeing unused kernel memory: 692K (ffff880001b53000 - ffff880001c00000)
[    0.912135] systemd-udevd[111]: starting version 204
[    0.913457] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.946123] ahci 0000:00:1f.2: version 3.0
[    0.946259] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[    0.949490] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.949499] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.949739] r8169 0000:03:00.0: irq 42 for MSI/MSI-X
[    0.949905] r8169 0000:03:00.0 eth0: RTL8168evl/8111evl at 0xffffc9000033c000, 3c:97:0e:bf:d6:51, XID 0c900800 IRQ 42
[    0.949908] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    0.962302] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0x11 impl SATA mode
[    0.962308] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    0.970661] scsi0 : ahci
[    0.972498] scsi1 : ahci
[    0.972683] scsi2 : ahci
[    0.974566] scsi3 : ahci
[    0.974717] scsi4 : ahci
[    0.974750] ata1: SATA max UDMA/133 abar m2048@0x90618000 port 0x90618100 irq 41
[    0.974752] ata2: DUMMY
[    0.974753] ata3: DUMMY
[    0.974754] ata4: DUMMY
[    0.974757] ata5: SATA max UDMA/133 abar m2048@0x90618000 port 0x90618300 irq 41
[    1.174394] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.294445] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.294483] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.298658] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.298666] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.298670] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.298976] ata5.00: ATAPI: PLDS DVD-RW DS8A9SH, EL3A, max UDMA/100
[    1.299285] ata1.00: ATA-9: WDC WD5000LPVX-22V0TT0, 01.01A01, max UDMA/133
[    1.299288] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.299785] ata5.00: configured for UDMA/100
[    1.299955] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.299962] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.299966] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.300597] ata1.00: configured for UDMA/133
[    1.300785] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000LPVX-2 01.0 PQ: 0 ANSI: 5
[    1.300916] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.301047] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.301049] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.301178] sd 0:0:0:0: [sda] Write Protect is off
[    1.301181] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.301254] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.306749] scsi 4:0:0:0: CD-ROM            PLDS     DVD-RW DS8A9SH   EL3A PQ: 0 ANSI: 5
[    1.306759] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.306761] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.307054] hub 1-1:1.0: USB hub found
[    1.307124] hub 1-1:1.0: 4 ports detected
[    1.314786] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.314789] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.314876] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.314921] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    1.383034]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.383580] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.418589] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.551111] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.551114] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.551362] hub 2-1:1.0: USB hub found
[    1.551451] hub 2-1:1.0: 4 ports detected
[    1.622767] usb 1-1.1: new high-speed USB device number 3 using ehci-pci
[    1.662730] tsc: Refined TSC clocksource calibration: 2394.561 MHz
[    1.706255] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xf00073/0x240000/0xa2400, board id: 2060, fw id: 1040538
[    1.726382] usb 1-1.1: New USB device found, idVendor=5986, idProduct=0295
[    1.726388] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.726392] usb 1-1.1: Product: Integrated Camera
[    1.726395] usb 1-1.1: Manufacturer: Vimicro corp.
[    1.739987] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    1.799151] usb 1-1.3: new high-speed USB device number 4 using ehci-pci
[    1.893284] usb 1-1.3: New USB device found, idVendor=058f, idProduct=6366
[    1.893290] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.893306] usb 1-1.3: Product: Flash Card Reader/Writer
[    1.893307] usb 1-1.3: Manufacturer: Generic
[    1.893309] usb 1-1.3: SerialNumber: 058F63666435
[    1.896097] usb-storage 1-1.3:1.0: USB Mass Storage device detected
[    1.896208] scsi5 : usb-storage 1-1.3:1.0
[    1.896260] usbcore: registered new interface driver usb-storage
[    1.963112] usb 1-1.4: new full-speed USB device number 5 using ehci-pci
[    2.057880] usb 1-1.4: New USB device found, idVendor=105b, idProduct=e065
[    2.057886] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.057889] usb 1-1.4: Product: BCM43142A0
[    2.057892] usb 1-1.4: Manufacturer: Broadcom Corp
[    2.057895] usb 1-1.4: SerialNumber: 1C3E84E7B5C4
[    2.398503] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    2.663755] Switched to clocksource tsc
[    2.709798] random: nonblocking pool is initialized
[    2.896671] scsi 5:0:0:0: Direct-Access     Multiple Card  Reader     1.00 PQ: 0 ANSI: 0
[    2.896875] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    2.898232] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[    3.530769] init: plymouth-upstart-bridge main process (176) terminated with status 1
[    3.530781] init: plymouth-upstart-bridge main process ended, respawning
[    3.533641] init: plymouth-upstart-bridge main process (187) terminated with status 1
[    3.533652] init: plymouth-upstart-bridge main process ended, respawning
[    3.535526] init: plymouth-upstart-bridge main process (189) terminated with status 1
[    3.535539] init: plymouth-upstart-bridge main process ended, respawning
[    3.537964] init: plymouth-upstart-bridge main process (190) terminated with status 1
[    3.537975] init: plymouth-upstart-bridge main process ended, respawning
[    3.539777] init: plymouth-upstart-bridge main process (192) terminated with status 1
[    3.539786] init: plymouth-upstart-bridge main process ended, respawning
[    3.542235] init: plymouth-upstart-bridge main process (193) terminated with status 1
[    3.542246] init: plymouth-upstart-bridge main process ended, respawning
[    3.544560] init: plymouth-upstart-bridge main process (195) terminated with status 1
[    3.544570] init: plymouth-upstart-bridge main process ended, respawning
[    3.547032] init: plymouth-upstart-bridge main process (196) terminated with status 1
[    3.547043] init: plymouth-upstart-bridge main process ended, respawning
[    3.548997] init: plymouth-upstart-bridge main process (198) terminated with status 1
[    3.549007] init: plymouth-upstart-bridge main process ended, respawning
[    3.551406] init: plymouth-upstart-bridge main process (199) terminated with status 1
[    3.551416] init: plymouth-upstart-bridge main process ended, respawning
[    3.553437] init: plymouth-upstart-bridge main process (201) terminated with status 1
[    3.553449] init: plymouth-upstart-bridge respawning too fast, stopped
[   13.810989] Adding 1665020k swap on /dev/sda6.  Priority:-1 extents:1 across:1665020k FS
[   13.873307] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.902212] systemd-udevd[300]: starting version 204
[   14.058864] wmi: Mapper loaded
[   14.066717] mei_me 0000:00:16.0: irq 43 for MSI/MSI-X
[   14.066898] [drm] Initialized drm 1.1.0 20060810
[   14.081893] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[   14.081900] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.081905] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   14.081908] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
[   14.081910] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.LPCB.LPIO 3 (20131115/utaddress-251)
[   14.081913] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.081914] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   14.081916] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
[   14.081918] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.LPCB.LPIO 3 (20131115/utaddress-251)
[   14.081921] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.081922] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   14.105867] cfg80211: Calling CRDA to update world regulatory domain
[   14.107557] [drm] Memory usable by graphics device = 2048M
[   14.107561] checking generic (80000000 410000) vs hw (80000000 10000000)
[   14.107562] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[   14.107578] Console: switching to colour dummy device 80x25
[   14.109772] lib80211: common routines for IEEE802.11 drivers
[   14.109775] lib80211_crypt: registered algorithm 'NULL'
[   14.111235] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.111238] Disabling lock debugging due to kernel taint
[   14.112912] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   14.153970] lp: driver loaded but no devices found
[   14.160671] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   14.162814] ppdev: user-space parallel port driver
[   14.168415] lib80211_crypt: registered algorithm 'TKIP'
[   14.215443] type=1400 audit(1414393275.804:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=353 comm="apparmor_parser"
[   14.215450] type=1400 audit(1414393275.804:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=353 comm="apparmor_parser"
[   14.215454] type=1400 audit(1414393275.804:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=353 comm="apparmor_parser"
[   14.215839] type=1400 audit(1414393275.804:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=353 comm="apparmor_parser"
[   14.215844] type=1400 audit(1414393275.804:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=353 comm="apparmor_parser"
[   14.216044] type=1400 audit(1414393275.804:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=353 comm="apparmor_parser"
[   14.286927] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   14.286938] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   14.286940] [drm] Driver supports precise vblank timestamp query.
[   14.287001] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   14.287329] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   14.303407] Non-volatile memory driver v1.3
[   14.306166] thinkpad_acpi: ThinkPad ACPI Extras v0.25
[   14.306169] thinkpad_acpi: http://ibm-acpi.sf.net/
[   14.306170] thinkpad_acpi: ThinkPad BIOS H9ET83WW(1.20), EC unknown
[   14.306171] thinkpad_acpi: Lenovo Lenovo B590, model 37613EG
[   14.309286] kvm: disabled by bios
[   14.310041] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   14.310131] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   14.310133] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   14.313190] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[   14.313763] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[   14.313842] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   14.315221] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input6
[   14.348170] fbcon: inteldrmfb (fb0) is primary device
[   14.471746] intel_rapl: domain uncore energy ctr 175539:175539 not working, skip
[   14.478518] Linux video capture interface: v2.00
[   14.484015] uvcvideo: Found UVC 1.00 device Integrated Camera (5986:0295)
[   14.485696] Bluetooth: Core ver 2.17
[   14.485730] NET: Registered protocol family 31
[   14.485730] Bluetooth: HCI device and connection manager initialized
[   14.485737] Bluetooth: HCI socket layer initialized
[   14.485738] Bluetooth: L2CAP socket layer initialized
[   14.485741] Bluetooth: SCO socket layer initialized
[   14.491048] usbcore: registered new interface driver btusb
[   14.491445] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input7
[   14.491535] usbcore: registered new interface driver uvcvideo
[   14.491536] USB Video Class driver (1.1.1)
[   14.519836] acer_wmi: Acer Laptop ACPI-WMI Extras
[   14.541892] acer_wmi: Brightness must be controlled by acpi video driver
[   14.542394] input: Acer BMA150 accelerometer as /devices/virtual/input/input8
[   14.577976] usb 1-1.4: Direct firmware load failed with error -2
[   14.577979] usb 1-1.4: Falling back to user helper
[   14.609834] cfg80211: World regulatory domain updated:
[   14.609835] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.609836] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.609837] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.609837] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.609838] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.609839] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.736882] Bluetooth: can't load firmware, may not work correctly
[   15.082229] Console: switching to colour frame buffer device 170x48
[   15.084754] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   15.084755] i915 0000:00:02.0: registered panic notifier
[   15.107646] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   15.123179] acpi device:47: registered as cooling_device3
[   15.123561] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input9
[   15.126673] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.127219] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   15.142844] SKU: Nid=0x1d sku_cfg=0x40130605
[   15.142847] SKU: port_connectivity=0x1
[   15.142848] SKU: enable_pcbeep=0x1
[   15.142849] SKU: check_sum=0x00000003
[   15.142850] SKU: customization=0x00000006
[   15.142850] SKU: external_amp=0x0
[   15.142851] SKU: platform_type=0x1
[   15.142852] SKU: swap=0x0
[   15.142853] SKU: override=0x1
[   15.143076] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   15.143077]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   15.143078]    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   15.143079]    mono: mono_out=0x0
[   15.143080]    inputs:
[   15.143081]      Internal Mic=0x19
[   15.143083]      Mic=0x18
[   15.143084] realtek: No valid SSID, checking pincfg 0x40130605 for NID 0x1d
[   15.143085] realtek: Enabling init ASM_ID=0x0605 CODEC_ID=10ec0269
[   15.157033] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   15.157235] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   15.157373] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   15.226999] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   15.831148] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[   15.912604] init: failsafe main process (603) killed by TERM signal
[   16.615030] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.615034] Bluetooth: BNEP filters: protocol multicast
[   16.615042] Bluetooth: BNEP socket layer initialized
[   16.618478] Bluetooth: RFCOMM TTY layer initialized
[   16.618488] Bluetooth: RFCOMM socket layer initialized
[   16.618494] Bluetooth: RFCOMM ver 1.11
[   16.743555] Bluetooth: hci0 command 0x1003 tx timeout
[   16.858932] type=1400 audit(1414393278.444:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=712 comm="apparmor_parser"
[   16.858941] type=1400 audit(1414393278.444:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=712 comm="apparmor_parser"
[   16.859331] type=1400 audit(1414393278.444:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=712 comm="apparmor_parser"
[   17.098302] init: cups main process (722) killed by HUP signal
[   17.098316] init: cups main process ended, respawning
[   18.755422] r8169 0000:03:00.0 eth0: link down
[   18.755468] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.756158] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.503284] type=1400 audit(1414393281.088:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=819 comm="apparmor_parser"
[   19.503293] type=1400 audit(1414393281.088:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=819 comm="apparmor_parser"
[   19.503297] type=1400 audit(1414393281.088:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=819 comm="apparmor_parser"
[   19.503685] type=1400 audit(1414393281.088:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=819 comm="apparmor_parser"
[   19.503689] type=1400 audit(1414393281.088:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=819 comm="apparmor_parser"
[   19.503828] type=1400 audit(1414393281.088:16): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=818 comm="apparmor_parser"
[   19.503835] type=1400 audit(1414393281.088:17): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=818 comm="apparmor_parser"
[   19.503890] type=1400 audit(1414393281.088:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=819 comm="apparmor_parser"
[   19.504078] type=1400 audit(1414393281.088:19): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=818 comm="apparmor_parser"
[   19.509517] type=1400 audit(1414393281.092:20): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=822 comm="apparmor_parser"
[   26.957381] init: anacron main process (994) killed by TERM signal
[   46.946256] audit_printk_skb: 123 callbacks suppressed
[   46.946260] type=1400 audit(1414393308.508:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1817 comm="apparmor_parser"
[   46.946266] type=1400 audit(1414393308.508:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1817 comm="apparmor_parser"
[   46.946655] type=1400 audit(1414393308.508:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1817 comm="apparmor_parser"
[   66.267580] cfg80211: Calling CRDA to update world regulatory domain
[   66.272035] cfg80211: World regulatory domain updated:
[   66.272038] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   66.272040] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   66.272042] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   66.272043] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   66.272044] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   66.272045] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  114.310769] cfg80211: Calling CRDA to update world regulatory domain
[  114.315693] cfg80211: World regulatory domain updated:
[  114.315699] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  114.315703] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  114.315705] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  114.315708] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  114.315710] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  114.315713] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  162.356866] cfg80211: Calling CRDA to update world regulatory domain
[  162.360667] cfg80211: World regulatory domain updated:
[  162.360671] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  162.360673] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  162.360674] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  162.360675] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  162.360677] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  162.360678] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  210.396775] cfg80211: Calling CRDA to update world regulatory domain
[  210.406130] cfg80211: World regulatory domain updated:
[  210.406136] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  210.406138] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  210.406141] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  210.406142] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  210.406144] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  210.406145] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)


```

It can still see the wifi (it´s the lodge_EXT):

[ATTACH=CONFIG]257518[/ATTACH]
But it keeps on showing this:

[ATTACH=CONFIG]257519[/ATTACH]

Unfortunatly I cannot manipulate the rooter itself, as this is a shared house and the owner does not allow it.

---

### Post by paul.zierep on 2014-10-27
PS.: I do get connected with my mobile phone just fine, my security is: WPA & WPA2 Personal

---

### Post by Bucky Ball on 2014-10-27
Give us dmesg AFTER it disconnects and only the last bit that should tell us what happened, or give some clue. 

So you are auto-connecting with a secure connection to 'lodge' at boot by the looks. Presume that's you. Then it drops?

Could you click the Network Manager icon and 'Edit' and check your wireless settings. Under IPv6 tab set it to 'Ignore' for now. Make sure the security is correct and matches your router's security. Under 'General' tab make sure 'Auto connect to this network' and 'All user may connect' are both checked. (Not Auto VPN.)  

Under Wifi tab set to Infrastructure. Are you using static IP or served from the router? Apologies if I already asked.

* If phone connecting we know it is not at the router end. That is good. ;)

---

### Post by paul.zierep on 2014-10-27
Hi I´ve done all that, except for the IPv6 everything was set so before, I changed the IPv6 to ignore.
I don´t know what static IP or served from the router means, respectively how to find that out :) 

Thanks

---

### Post by Bucky Ball on 2014-10-27
IPv4 tab in Network Manager. Is 'Method' set to Automatic (DHCP) or Manual?

---

### Post by paul.zierep on 2014-10-27
Automatic (DHCP)

---

### Post by paul.zierep on 2014-10-27
So it just disconnected and this is what I get for dmesg :
```

[    0.882442] uhci_hcd: USB Universal Host Controller Interface driver
[    0.882539] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.882543] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.882639] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.882663] xhci_hcd 0000:00:14.0: irq 40 for MSI/MSI-X
[    0.882722] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.882723] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.882725] usb usb3: Product: xHCI Host Controller
[    0.882726] usb usb3: Manufacturer: Linux 3.13.0-37-generic xhci_hcd
[    0.882728] usb usb3: SerialNumber: 0000:00:14.0
[    0.882879] hub 3-0:1.0: USB hub found
[    0.882890] hub 3-0:1.0: 4 ports detected
[    0.883200] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.883203] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.883237] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.883238] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.883240] usb usb4: Product: xHCI Host Controller
[    0.883241] usb usb4: Manufacturer: Linux 3.13.0-37-generic xhci_hcd
[    0.883242] usb usb4: SerialNumber: 0000:00:14.0
[    0.883386] hub 4-0:1.0: USB hub found
[    0.883398] hub 4-0:1.0: 4 ports detected
[    0.890221] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.893499] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.893504] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.893688] mousedev: PS/2 mouse device common for all mice
[    0.893932] rtc_cmos 00:06: RTC can wake from S4
[    0.894049] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.894079] rtc_cmos 00:06: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.894150] device-mapper: uevent: version 1.0.3
[    0.894203] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.894209] ledtrig-cpu: registered to indicate activity on CPUs
[    0.894292] TCP: cubic registered
[    0.894362] NET: Registered protocol family 10
[    0.894507] NET: Registered protocol family 17
[    0.894518] Key type dns_resolver registered
[    0.894733] Loading compiled-in X.509 certificates
[    0.895569] Loaded X.509 cert 'Magrathea: Glacier signing key: 2cb1133b35f95a9e24deabeeb12ba449bcbabbc9'
[    0.895579] registered taskstats version 1
[    0.897415] Key type trusted registered
[    0.898921] Key type encrypted registered
[    0.900435] AppArmor: AppArmor sha1 policy hashing enabled
[    0.900438] IMA: No TPM chip found, activating TPM-bypass!
[    0.900717] regulator-dummy: disabling
[    0.900748]   Magic number: 2:339:444
[    0.900830] rtc_cmos 00:06: setting system clock to 2014-10-27 18:24:52 UTC (1414434292)
[    0.901129] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.901130] EDD information not available.
[    0.901167] PM: Hibernation image not present or could not be loaded.
[    0.901999] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    0.902001] Write protecting the kernel read-only data: 12288k
[    0.903919] Freeing unused kernel memory: 804K (ffff880001737000 - ffff880001800000)
[    0.905544] Freeing unused kernel memory: 692K (ffff880001b53000 - ffff880001c00000)
[    0.915645] systemd-udevd[110]: starting version 204
[    0.926221] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.933416] ahci 0000:00:1f.2: version 3.0
[    0.933552] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[    0.940314] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.940324] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.940577] r8169 0000:03:00.0: irq 42 for MSI/MSI-X
[    0.940750] r8169 0000:03:00.0 eth0: RTL8168evl/8111evl at 0xffffc9000033c000, 3c:97:0e:bf:d6:51, XID 0c900800 IRQ 42
[    0.940752] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    0.946198] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0x11 impl SATA mode
[    0.946202] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    0.955337] scsi0 : ahci
[    0.955400] scsi1 : ahci
[    0.955451] scsi2 : ahci
[    0.955498] scsi3 : ahci
[    0.955546] scsi4 : ahci
[    0.955577] ata1: SATA max UDMA/133 abar m2048@0x90618000 port 0x90618100 irq 41
[    0.955578] ata2: DUMMY
[    0.955579] ata3: DUMMY
[    0.955580] ata4: DUMMY
[    0.955583] ata5: SATA max UDMA/133 abar m2048@0x90618000 port 0x90618300 irq 41
[    1.178426] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.274517] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.278651] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.278694] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.278698] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.278700] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.279340] ata1.00: ATA-9: WDC WD5000LPVX-22V0TT0, 01.01A01, max UDMA/133
[    1.279343] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.280000] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.280008] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.280024] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.280611] ata1.00: configured for UDMA/133
[    1.280785] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000LPVX-2 01.0 PQ: 0 ANSI: 5
[    1.280937] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.280939] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.280960] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.281017] sd 0:0:0:0: [sda] Write Protect is off
[    1.281020] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.281041] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.282512] ata5.00: ATAPI: PLDS DVD-RW DS8A9SH, EL3A, max UDMA/100
[    1.283203] ata5.00: configured for UDMA/100
[    1.284786] scsi 4:0:0:0: CD-ROM            PLDS     DVD-RW DS8A9SH   EL3A PQ: 0 ANSI: 5
[    1.292792] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.292797] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.292955] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.293006] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    1.310916] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.310934] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.311170] hub 1-1:1.0: USB hub found
[    1.311252] hub 1-1:1.0: 4 ports detected
[    1.371811]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.372365] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.422635] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.555106] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.555113] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.555357] hub 2-1:1.0: USB hub found
[    1.555447] hub 2-1:1.0: 4 ports detected
[    1.626885] usb 1-1.1: new high-speed USB device number 3 using ehci-pci
[    1.662800] tsc: Refined TSC clocksource calibration: 2394.560 MHz
[    1.717013] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xf00073/0x240000/0xa2400, board id: 2060, fw id: 1040538
[    1.730490] usb 1-1.1: New USB device found, idVendor=5986, idProduct=0295
[    1.730496] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.730499] usb 1-1.1: Product: Integrated Camera
[    1.730502] usb 1-1.1: Manufacturer: Vimicro corp.
[    1.751542] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    1.803065] usb 1-1.3: new high-speed USB device number 4 using ehci-pci
[    1.897488] usb 1-1.3: New USB device found, idVendor=058f, idProduct=6366
[    1.897494] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.897497] usb 1-1.3: Product: Flash Card Reader/Writer
[    1.897500] usb 1-1.3: Manufacturer: Generic
[    1.897503] usb 1-1.3: SerialNumber: 058F63666435
[    1.900193] usb-storage 1-1.3:1.0: USB Mass Storage device detected
[    1.900252] scsi5 : usb-storage 1-1.3:1.0
[    1.900304] usbcore: registered new interface driver usb-storage
[    1.967257] usb 1-1.4: new full-speed USB device number 5 using ehci-pci
[    2.061741] usb 1-1.4: New USB device found, idVendor=105b, idProduct=e065
[    2.061744] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.061746] usb 1-1.4: Product: BCM43142A0
[    2.061748] usb 1-1.4: Manufacturer: Broadcom Corp
[    2.061749] usb 1-1.4: SerialNumber: 1C3E84E7B5C4
[    2.553487] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    2.604999] random: nonblocking pool is initialized
[    2.663738] Switched to clocksource tsc
[    2.900651] scsi 5:0:0:0: Direct-Access     Multiple Card  Reader     1.00 PQ: 0 ANSI: 0
[    2.900847] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    2.902354] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[    3.674719] init: plymouth-upstart-bridge main process (177) terminated with status 1
[    3.674731] init: plymouth-upstart-bridge main process ended, respawning
[    3.677612] init: plymouth-upstart-bridge main process (188) terminated with status 1
[    3.677623] init: plymouth-upstart-bridge main process ended, respawning
[    3.679453] init: plymouth-upstart-bridge main process (190) terminated with status 1
[    3.679466] init: plymouth-upstart-bridge main process ended, respawning
[    3.681866] init: plymouth-upstart-bridge main process (191) terminated with status 1
[    3.681876] init: plymouth-upstart-bridge main process ended, respawning
[    3.683654] init: plymouth-upstart-bridge main process (193) terminated with status 1
[    3.683663] init: plymouth-upstart-bridge main process ended, respawning
[    3.686088] init: plymouth-upstart-bridge main process (194) terminated with status 1
[    3.686099] init: plymouth-upstart-bridge main process ended, respawning
[    3.687864] init: plymouth-upstart-bridge main process (196) terminated with status 1
[    3.687873] init: plymouth-upstart-bridge main process ended, respawning
[    3.690233] init: plymouth-upstart-bridge main process (197) terminated with status 1
[    3.690243] init: plymouth-upstart-bridge main process ended, respawning
[    3.691986] init: plymouth-upstart-bridge main process (199) terminated with status 1
[    3.691995] init: plymouth-upstart-bridge main process ended, respawning
[    3.694346] init: plymouth-upstart-bridge main process (200) terminated with status 1
[    3.694357] init: plymouth-upstart-bridge main process ended, respawning
[    3.696087] init: plymouth-upstart-bridge main process (202) terminated with status 1
[    3.696096] init: plymouth-upstart-bridge respawning too fast, stopped
[   13.555865] Adding 1665020k swap on /dev/sda6.  Priority:-1 extents:1 across:1665020k FS
[   13.607239] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.674545] systemd-udevd[305]: starting version 204
[   13.789974] lp: driver loaded but no devices found
[   13.795944] ppdev: user-space parallel port driver
[   13.812517] [drm] Initialized drm 1.1.0 20060810
[   13.830746] [drm] Memory usable by graphics device = 2048M
[   13.830750] checking generic (80000000 410000) vs hw (80000000 10000000)
[   13.830752] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[   13.830770] Console: switching to colour dummy device 80x25
[   13.874577] wmi: Mapper loaded
[   13.882477] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[   13.882487] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   13.882489] [drm] Driver supports precise vblank timestamp query.
[   13.882546] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   13.893023] cfg80211: Calling CRDA to update world regulatory domain
[   13.894925] lib80211: common routines for IEEE802.11 drivers
[   13.894929] lib80211_crypt: registered algorithm 'NULL'
[   13.896430] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.896434] Disabling lock debugging due to kernel taint
[   13.902361] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   13.939836] fbcon: inteldrmfb (fb0) is primary device
[   13.939901] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   13.947615] lib80211_crypt: registered algorithm 'TKIP'
[   14.003834] type=1400 audit(1414398305.588:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=357 comm="apparmor_parser"
[   14.003839] type=1400 audit(1414398305.588:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=357 comm="apparmor_parser"
[   14.003842] type=1400 audit(1414398305.588:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=357 comm="apparmor_parser"
[   14.004227] type=1400 audit(1414398305.588:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=357 comm="apparmor_parser"
[   14.004231] type=1400 audit(1414398305.588:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=357 comm="apparmor_parser"
[   14.004430] type=1400 audit(1414398305.588:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=357 comm="apparmor_parser"
[   14.043541] kvm: disabled by bios
[   14.063430] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   14.068506] Non-volatile memory driver v1.3
[   14.072835] thinkpad_acpi: ThinkPad ACPI Extras v0.25
[   14.072836] thinkpad_acpi: http://ibm-acpi.sf.net/
[   14.072836] thinkpad_acpi: ThinkPad BIOS H9ET83WW(1.20), EC unknown
[   14.072837] thinkpad_acpi: Lenovo Lenovo B590, model 37613EG
[   14.073294] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   14.073399] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   14.073399] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   14.076351] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[   14.077051] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[   14.077135] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   14.079747] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input6
[   14.205471] intel_rapl: domain uncore energy ctr 215631:215631 not working, skip
[   14.256199] Linux video capture interface: v2.00
[   14.264205] uvcvideo: Found UVC 1.00 device Integrated Camera (5986:0295)
[   14.265166] Bluetooth: Core ver 2.17
[   14.265542] NET: Registered protocol family 31
[   14.265543] Bluetooth: HCI device and connection manager initialized
[   14.265549] Bluetooth: HCI socket layer initialized
[   14.265551] Bluetooth: L2CAP socket layer initialized
[   14.265555] Bluetooth: SCO socket layer initialized
[   14.266021] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input7
[   14.266081] usbcore: registered new interface driver uvcvideo
[   14.266082] USB Video Class driver (1.1.1)
[   14.270119] usbcore: registered new interface driver btusb
[   14.422068] usb 1-1.4: Direct firmware load failed with error -2
[   14.422070] usb 1-1.4: Falling back to user helper
[   14.637915] Console: switching to colour frame buffer device 170x48
[   14.640473] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   14.640474] i915 0000:00:02.0: registered panic notifier
[   14.679104] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   14.702899] acer_wmi: Acer Laptop ACPI-WMI Extras
[   14.714450] acpi device:47: registered as cooling_device3
[   14.714899] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8
[   14.715167] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   14.715334] mei_me 0000:00:16.0: irq 44 for MSI/MSI-X
[   14.719655] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[   14.719662] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.719666] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   14.719668] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
[   14.719671] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.LPCB.LPIO 3 (20131115/utaddress-251)
[   14.719673] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.719675] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   14.719677] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
[   14.719679] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.LPCB.LPIO 3 (20131115/utaddress-251)
[   14.719681] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.719683] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   14.742412] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   14.742614] acer_wmi: Brightness must be controlled by acpi video driver
[   14.743607] input: Acer BMA150 accelerometer as /devices/virtual/input/input9
[   14.767771] Bluetooth: can't load firmware, may not work correctly
[   14.769437] SKU: Nid=0x1d sku_cfg=0x40130605
[   14.769440] SKU: port_connectivity=0x1
[   14.769441] SKU: enable_pcbeep=0x1
[   14.769442] SKU: check_sum=0x00000003
[   14.769443] SKU: customization=0x00000006
[   14.769444] SKU: external_amp=0x0
[   14.769445] SKU: platform_type=0x1
[   14.769445] SKU: swap=0x0
[   14.769446] SKU: override=0x1
[   14.769691] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   14.769692]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   14.769694]    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   14.769694]    mono: mono_out=0x0
[   14.769695]    inputs:
[   14.769697]      Internal Mic=0x19
[   14.769698]      Mic=0x18
[   14.769700] realtek: No valid SSID, checking pincfg 0x40130605 for NID 0x1d
[   14.769701] realtek: Enabling init ASM_ID=0x0605 CODEC_ID=10ec0269
[   14.792350] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   14.792508] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   14.792647] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   14.953227] cfg80211: World regulatory domain updated:
[   14.953231] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.953233] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.953234] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.953235] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.953236] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.953238] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.278893] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   15.715299] init: failsafe main process (630) killed by TERM signal
[   15.831172] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[   16.416289] Bluetooth: RFCOMM TTY layer initialized
[   16.416301] Bluetooth: RFCOMM socket layer initialized
[   16.416305] Bluetooth: RFCOMM ver 1.11
[   16.487767] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.487770] Bluetooth: BNEP filters: protocol multicast
[   16.487778] Bluetooth: BNEP socket layer initialized
[   16.611398] init: avahi-cups-reload main process (729) terminated with status 1
[   16.637099] type=1400 audit(1414398308.220:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=710 comm="apparmor_parser"
[   16.637107] type=1400 audit(1414398308.220:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=710 comm="apparmor_parser"
[   16.637492] type=1400 audit(1414398308.220:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=710 comm="apparmor_parser"
[   16.775633] Bluetooth: hci0 command 0x1003 tx timeout
[   18.041715] type=1400 audit(1414398309.624:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=809 comm="apparmor_parser"
[   18.042780] r8169 0000:03:00.0 eth0: link down
[   18.042827] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.043699] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.782177] init: anacron main process (993) killed by TERM signal
[  106.497515] systemd-hostnamed[2028]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 3120.916644] systemd-hostnamed[2684]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 4744.738021] cfg80211: Calling CRDA to update world regulatory domain
[ 4745.682115] cfg80211: World regulatory domain updated:
[ 4745.682119] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4745.682121] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4745.682122] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4745.682123] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4745.682125] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4745.682126] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5586.452782] cfg80211: Calling CRDA to update world regulatory domain
[ 5587.105138] cfg80211: World regulatory domain updated:
[ 5587.105142] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 5587.105144] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5587.105145] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5587.105146] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 5587.105148] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 5587.105149] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7348.571990] audit_printk_skb: 150 callbacks suppressed
[ 7348.571994] type=1400 audit(1414405634.384:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=3569 comm="apparmor_parser"
[ 7348.572000] type=1400 audit(1414405634.384:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3569 comm="apparmor_parser"
[ 7348.572387] type=1400 audit(1414405634.384:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3569 comm="apparmor_parser"
[ 7380.399697] perf samples too long (2587 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 8424.890284] systemd-hostnamed[3770]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[11340.150574] cfg80211: Calling CRDA to update world regulatory domain
[11341.597294] cfg80211: World regulatory domain updated:
[11341.597298] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[11341.597301] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11341.597302] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11341.597304] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[11341.597305] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11341.597307] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11390.437049] cfg80211: Calling CRDA to update world regulatory domain
[11390.440350] cfg80211: World regulatory domain updated:
[11390.440353] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[11390.440355] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11390.440357] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11390.440358] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[11390.440359] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11390.440360] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11438.478042] cfg80211: Calling CRDA to update world regulatory domain
[11438.480729] cfg80211: World regulatory domain updated:
[11438.480733] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[11438.480735] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11438.480736] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11438.480738] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[11438.480739] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11438.480740] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11486.518929] cfg80211: Calling CRDA to update world regulatory domain
[11486.521519] cfg80211: World regulatory domain updated:
[11486.521523] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[11486.521524] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11486.521526] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11486.521527] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[11486.521528] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11486.521530] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11534.559380] cfg80211: Calling CRDA to update world regulatory domain
[11534.562821] cfg80211: World regulatory domain updated:
[11534.562824] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[11534.562826] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11534.562828] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11534.562829] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[11534.562830] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11534.562831] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)


```

---

### Post by slickymaster on 2014-10-27
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by Bucky Ball on 2014-10-27
Looks like, as in the last one, you are missing the important bit: the last part where you are back at the cursor in a terminal. Don't want the whole thing, just that bit. Try again and when it disconnects, dmesg, scroll down to the end of the message, have a look for anything that relates to the wireless (it will be the last section, probably less than thirty lines) and post that.

Thanks. We'll keep tryin'. ;)

PS: Thanks slickymaster. For some reason I thought I already moved here. That's one comes from doin' five things at once! That will improve chances.

---

### Post by paul.zierep on 2014-10-28
Ok, sorry I thought I had all of it....I´ll do it next time ! Thank you !

---

### Post by paul.zierep on 2014-10-30
So again dmesg, sorry that I do the whole text again, I just don´t really know what we´re looking for. This is the whole text:

```

evel@redhat.com
[    0.890180] ledtrig-cpu: registered to indicate activity on CPUs
[    0.890264] TCP: cubic registered
[    0.890334] NET: Registered protocol family 10
[    0.890481] NET: Registered protocol family 17
[    0.890488] Key type dns_resolver registered
[    0.890647] Loading compiled-in X.509 certificates
[    0.891483] Loaded X.509 cert 'Magrathea: Glacier signing key: 2cb1133b35f95a9e24deabeeb12ba449bcbabbc9'
[    0.891493] registered taskstats version 1
[    0.893321] Key type trusted registered
[    0.894817] Key type encrypted registered
[    0.896343] AppArmor: AppArmor sha1 policy hashing enabled
[    0.896346] IMA: No TPM chip found, activating TPM-bypass!
[    0.896628] regulator-dummy: disabling
[    0.896664]   Magic number: 2:183:42
[    0.896673] bdi 7:7: hash matches
[    0.896750] rtc_cmos 00:06: setting system clock to 2014-10-29 19:00:50 UTC (1414609250)
[    0.897062] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.897063] EDD information not available.
[    0.897101] PM: Hibernation image not present or could not be loaded.
[    0.897949] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    0.897950] Write protecting the kernel read-only data: 12288k
[    0.899895] Freeing unused kernel memory: 804K (ffff880001737000 - ffff880001800000)
[    0.901537] Freeing unused kernel memory: 692K (ffff880001b53000 - ffff880001c00000)
[    0.911909] systemd-udevd[110]: starting version 204
[    0.917044] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.940841] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.940851] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.941103] r8169 0000:03:00.0: irq 41 for MSI/MSI-X
[    0.941263] r8169 0000:03:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000334000, 3c:97:0e:bf:d6:51, XID 0c900800 IRQ 41
[    0.941265] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    0.944386] ahci 0000:00:1f.2: version 3.0
[    0.944502] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    0.958257] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0x11 impl SATA mode
[    0.958262] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    0.966609] scsi0 : ahci
[    0.966680] scsi1 : ahci
[    0.966731] scsi2 : ahci
[    0.966779] scsi3 : ahci
[    0.966828] scsi4 : ahci
[    0.966858] ata1: SATA max UDMA/133 abar m2048@0x90618000 port 0x90618100 irq 42
[    0.966860] ata2: DUMMY
[    0.966861] ata3: DUMMY
[    0.966862] ata4: DUMMY
[    0.966865] ata5: SATA max UDMA/133 abar m2048@0x90618000 port 0x90618300 irq 42
[    1.174416] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.286484] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.286512] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.290581] ata5.00: ATAPI: PLDS DVD-RW DS8A9SH, EL3A, max UDMA/100
[    1.290626] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.290629] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.290631] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.291275] ata1.00: ATA-9: WDC WD5000LPVX-22V0TT0, 01.01A01, max UDMA/133
[    1.291291] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.291978] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.291985] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.291989] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.292566] ata1.00: configured for UDMA/133
[    1.292740] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000LPVX-2 01.0 PQ: 0 ANSI: 5
[    1.292878] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.292880] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.292912] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.292937] sd 0:0:0:0: [sda] Write Protect is off
[    1.292939] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.292959] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.296422] ata5.00: configured for UDMA/100
[    1.303364] scsi 4:0:0:0: CD-ROM            PLDS     DVD-RW DS8A9SH   EL3A PQ: 0 ANSI: 5
[    1.306831] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.306850] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.307089] hub 1-1:1.0: USB hub found
[    1.307153] hub 1-1:1.0: 4 ports detected
[    1.312008] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.312013] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.312109] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.312155] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    1.383385]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.383952] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.418593] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.551079] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.551082] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.551430] hub 2-1:1.0: USB hub found
[    1.551483] hub 2-1:1.0: 4 ports detected
[    1.622802] usb 1-1.1: new high-speed USB device number 3 using ehci-pci
[    1.662746] tsc: Refined TSC clocksource calibration: 2394.560 MHz
[    1.703851] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xf00073/0x240000/0xa2400, board id: 2060, fw id: 1040538
[    1.726387] usb 1-1.1: New USB device found, idVendor=5986, idProduct=0295
[    1.726393] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.726396] usb 1-1.1: Product: Integrated Camera
[    1.726399] usb 1-1.1: Manufacturer: Vimicro corp.
[    1.738052] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    1.802988] usb 1-1.3: new high-speed USB device number 4 using ehci-pci
[    1.897176] usb 1-1.3: New USB device found, idVendor=058f, idProduct=6366
[    1.897179] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.897181] usb 1-1.3: Product: Flash Card Reader/Writer
[    1.897182] usb 1-1.3: Manufacturer: Generic
[    1.897184] usb 1-1.3: SerialNumber: 058F63666435
[    1.899903] usb-storage 1-1.3:1.0: USB Mass Storage device detected
[    1.900001] scsi5 : usb-storage 1-1.3:1.0
[    1.900078] usbcore: registered new interface driver usb-storage
[    1.967118] usb 1-1.4: new full-speed USB device number 5 using ehci-pci
[    2.062311] usb 1-1.4: New USB device found, idVendor=105b, idProduct=e065
[    2.062317] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.062321] usb 1-1.4: Product: BCM43142A0
[    2.062324] usb 1-1.4: Manufacturer: Broadcom Corp
[    2.062326] usb 1-1.4: SerialNumber: 1C3E84E7B5C4
[    2.254826] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    2.663758] Switched to clocksource tsc
[    2.676798] random: nonblocking pool is initialized
[    2.900400] scsi 5:0:0:0: Direct-Access     Multiple Card  Reader     1.00 PQ: 0 ANSI: 0
[    2.900582] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    2.901890] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[    3.398173] init: plymouth-upstart-bridge main process (177) terminated with status 1
[    3.398186] init: plymouth-upstart-bridge main process ended, respawning
[    3.400740] init: plymouth-upstart-bridge main process (188) terminated with status 1
[    3.400751] init: plymouth-upstart-bridge main process ended, respawning
[    3.402567] init: plymouth-upstart-bridge main process (190) terminated with status 1
[    3.402576] init: plymouth-upstart-bridge main process ended, respawning
[    3.405046] init: plymouth-upstart-bridge main process (191) terminated with status 1
[    3.405057] init: plymouth-upstart-bridge main process ended, respawning
[    3.406878] init: plymouth-upstart-bridge main process (193) terminated with status 1
[    3.406891] init: plymouth-upstart-bridge main process ended, respawning
[    3.410514] init: plymouth-upstart-bridge main process (194) terminated with status 1
[    3.410525] init: plymouth-upstart-bridge main process ended, respawning
[    3.413379] init: plymouth-upstart-bridge main process (196) terminated with status 1
[    3.413390] init: plymouth-upstart-bridge main process ended, respawning
[    3.414998] init: plymouth-upstart-bridge main process (198) terminated with status 1
[    3.415008] init: plymouth-upstart-bridge main process ended, respawning
[    3.417224] init: plymouth-upstart-bridge main process (199) terminated with status 1
[    3.417234] init: plymouth-upstart-bridge main process ended, respawning
[    3.418951] init: plymouth-upstart-bridge main process (201) terminated with status 1
[    3.418961] init: plymouth-upstart-bridge main process ended, respawning
[    3.421052] init: plymouth-upstart-bridge main process (202) terminated with status 1
[    3.421062] init: plymouth-upstart-bridge respawning too fast, stopped
[   12.094017] Adding 1665020k swap on /dev/sda6.  Priority:-1 extents:1 across:1665020k FS
[   12.156238] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.234524] systemd-udevd[306]: starting version 204
[   12.380329] wmi: Mapper loaded
[   12.403722] mei_me 0000:00:16.0: irq 43 for MSI/MSI-X
[   12.406120] [drm] Initialized drm 1.1.0 20060810
[   12.410257] cfg80211: Calling CRDA to update world regulatory domain
[   12.421494] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[   12.421500] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.421505] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   12.421508] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
[   12.421510] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.LPCB.LPIO 3 (20131115/utaddress-251)
[   12.421513] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.421514] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   12.421516] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
[   12.421519] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.LPCB.LPIO 3 (20131115/utaddress-251)
[   12.421521] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.421522] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   12.422622] lib80211: common routines for IEEE802.11 drivers
[   12.422625] lib80211_crypt: registered algorithm 'NULL'
[   12.424778] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.424781] Disabling lock debugging due to kernel taint
[   12.431728] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   12.448645] [drm] Memory usable by graphics device = 2048M
[   12.448650] checking generic (80000000 410000) vs hw (80000000 10000000)
[   12.448651] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[   12.448666] Console: switching to colour dummy device 80x25
[   12.473249] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   12.475488] lib80211_crypt: registered algorithm 'TKIP'
[   12.530758] type=1400 audit(1414573262.117:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=351 comm="apparmor_parser"
[   12.530765] type=1400 audit(1414573262.117:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=351 comm="apparmor_parser"
[   12.530768] type=1400 audit(1414573262.117:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=351 comm="apparmor_parser"
[   12.531155] type=1400 audit(1414573262.117:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=351 comm="apparmor_parser"
[   12.531159] type=1400 audit(1414573262.117:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=351 comm="apparmor_parser"
[   12.531358] type=1400 audit(1414573262.117:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=351 comm="apparmor_parser"
[   12.595375] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   12.596392] lp: driver loaded but no devices found
[   12.605328] ppdev: user-space parallel port driver
[   12.608248] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   12.608258] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   12.608259] [drm] Driver supports precise vblank timestamp query.
[   12.608322] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   12.646337] Linux video capture interface: v2.00
[   12.648948] Non-volatile memory driver v1.3
[   12.651424] thinkpad_acpi: ThinkPad ACPI Extras v0.25
[   12.651427] thinkpad_acpi: http://ibm-acpi.sf.net/
[   12.651428] thinkpad_acpi: ThinkPad BIOS H9ET83WW(1.20), EC unknown
[   12.651429] thinkpad_acpi: Lenovo Lenovo B590, model 37613EG
[   12.651703] kvm: disabled by bios
[   12.652155] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   12.652248] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   12.652250] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   12.654325] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[   12.655843] Bluetooth: Core ver 2.17
[   12.655858] NET: Registered protocol family 31
[   12.655859] Bluetooth: HCI device and connection manager initialized
[   12.655866] Bluetooth: HCI socket layer initialized
[   12.655868] Bluetooth: L2CAP socket layer initialized
[   12.655871] Bluetooth: SCO socket layer initialized
[   12.657624] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[   12.657701] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   12.658135] uvcvideo: Found UVC 1.00 device Integrated Camera (5986:0295)
[   12.659021] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input6
[   12.661054] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input7
[   12.661111] usbcore: registered new interface driver uvcvideo
[   12.661113] USB Video Class driver (1.1.1)
[   12.661282] usbcore: registered new interface driver btusb
[   12.680748] fbcon: inteldrmfb (fb0) is primary device
[   12.803289] intel_rapl: domain uncore energy ctr 239922:239922 not working, skip
[   12.815228] acer_wmi: Acer Laptop ACPI-WMI Extras
[   12.832489] acer_wmi: Brightness must be controlled by acpi video driver
[   12.832776] input: Acer BMA150 accelerometer as /devices/virtual/input/input8
[   12.860695] usb 1-1.4: Direct firmware load failed with error -2
[   12.860697] usb 1-1.4: Falling back to user helper
[   12.970696] cfg80211: World regulatory domain updated:
[   12.970697] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.970700] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.970700] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.970701] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.970702] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.970703] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.067798] Bluetooth: can't load firmware, may not work correctly
[   13.452879] Console: switching to colour frame buffer device 170x48
[   13.455397] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   13.455398] i915 0000:00:02.0: registered panic notifier
[   13.465465] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   13.486484] acpi device:47: registered as cooling_device3
[   13.487106] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input9
[   13.488364] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   13.488554] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   13.510622] SKU: Nid=0x1d sku_cfg=0x40130605
[   13.510625] SKU: port_connectivity=0x1
[   13.510626] SKU: enable_pcbeep=0x1
[   13.510627] SKU: check_sum=0x00000003
[   13.510628] SKU: customization=0x00000006
[   13.510629] SKU: external_amp=0x0
[   13.510630] SKU: platform_type=0x1
[   13.510631] SKU: swap=0x0
[   13.510632] SKU: override=0x1
[   13.510847] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   13.510849]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   13.510850]    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   13.510851]    mono: mono_out=0x0
[   13.510852]    inputs:
[   13.510853]      Internal Mic=0x19
[   13.510854]      Mic=0x18
[   13.510856] realtek: No valid SSID, checking pincfg 0x40130605 for NID 0x1d
[   13.510857] realtek: Enabling init ASM_ID=0x0605 CODEC_ID=10ec0269
[   13.523549] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   13.523844] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   13.523935] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   13.829508] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[   14.060622] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   14.391285] init: failsafe main process (652) killed by TERM signal
[   15.607767] Bluetooth: RFCOMM TTY layer initialized
[   15.607777] Bluetooth: RFCOMM socket layer initialized
[   15.607781] Bluetooth: RFCOMM ver 1.11
[   15.746018] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.746021] Bluetooth: BNEP filters: protocol multicast
[   15.746030] Bluetooth: BNEP socket layer initialized
[   15.906511] type=1400 audit(1414573265.493:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=718 comm="apparmor_parser"
[   15.906519] type=1400 audit(1414573265.493:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=718 comm="apparmor_parser"
[   15.906915] type=1400 audit(1414573265.493:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=718 comm="apparmor_parser"
[   16.035751] init: cups main process (728) killed by HUP signal
[   16.035762] init: cups main process ended, respawning
[   17.476640] type=1400 audit(1414573267.061:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=815 comm="apparmor_parser"
[   17.536270] audit_printk_skb: 105 callbacks suppressed
[   17.536276] type=1400 audit(1414573267.121:47): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="sanitized_helper" pid=817 comm="apparmor_parser"
[   17.536294] type=1400 audit(1414573267.121:48): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/bin/evince-thumbnailer" pid=817 comm="apparmor_parser"
[   17.548311] type=1400 audit(1414573267.133:49): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="sanitized_helper" pid=817 comm="apparmor_parser"
[   17.548350] type=1400 audit(1414573267.133:50): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=820 comm="apparmor_parser"
[   17.549852] type=1400 audit(1414573267.133:51): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="sanitized_helper" pid=817 comm="apparmor_parser"
[   17.549857] type=1400 audit(1414573267.133:52): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/bin/evince-thumbnailer" pid=817 comm="apparmor_parser"
[   17.568397] type=1400 audit(1414573267.153:53): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="sanitized_helper" pid=817 comm="apparmor_parser"
[   17.568428] type=1400 audit(1414573267.153:54): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=821 comm="apparmor_parser"
[   17.568436] type=1400 audit(1414573267.153:55): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=821 comm="apparmor_parser"
[   17.568913] type=1400 audit(1414573267.153:56): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=821 comm="apparmor_parser"
[   17.738884] r8169 0000:03:00.0 eth0: link down
[   17.738930] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.739786] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   45.995079] audit_printk_skb: 15 callbacks suppressed
[   45.995082] type=1400 audit(1414573295.553:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1803 comm="apparmor_parser"
[   45.995089] type=1400 audit(1414573295.553:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1803 comm="apparmor_parser"
[   45.995476] type=1400 audit(1414573295.553:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1803 comm="apparmor_parser"
[   65.269248] cfg80211: Calling CRDA to update world regulatory domain
[   65.271992] cfg80211: World regulatory domain updated:
[   65.271995] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   65.271997] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   65.271999] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   65.272000] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   65.272002] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   65.272003] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  113.311888] cfg80211: Calling CRDA to update world regulatory domain
[  113.314340] cfg80211: World regulatory domain updated:
[  113.314343] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  113.314345] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  113.314347] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  113.314349] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  113.314350] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  113.314351] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  161.352854] cfg80211: Calling CRDA to update world regulatory domain
[  161.356209] cfg80211: World regulatory domain updated:
[  161.356213] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  161.356214] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  161.356216] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  161.356217] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  161.356218] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  161.356219] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  209.392185] cfg80211: Calling CRDA to update world regulatory domain
[  209.395200] cfg80211: World regulatory domain updated:
[  209.395204] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  209.395207] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  209.395209] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  209.395210] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  209.395212] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  209.395213] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3909.214318] cfg80211: Calling CRDA to update world regulatory domain
[ 3909.986658] cfg80211: World regulatory domain updated:
[ 3909.986662] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3909.986664] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3909.986665] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3909.986666] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3909.986667] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3909.986669] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3923.274170] cfg80211: Calling CRDA to update world regulatory domain
[ 3924.023793] cfg80211: World regulatory domain updated:
[ 3924.023798] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3924.023800] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3924.023801] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3924.023802] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3924.023804] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3924.023805] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6735.219740] systemd-hostnamed[3217]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 6846.680592] cfg80211: Calling CRDA to update world regulatory domain
[ 6847.304695] cfg80211: World regulatory domain updated:
[ 6847.304699] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 6847.304701] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6847.304703] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6847.304704] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 6847.304705] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6847.304706] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6896.026540] cfg80211: Calling CRDA to update world regulatory domain
[ 6896.029686] cfg80211: World regulatory domain updated:
[ 6896.029690] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 6896.029692] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6896.029694] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6896.029696] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 6896.029698] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6896.029699] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
paul@paul-Lenovo:~$ 


```

---

