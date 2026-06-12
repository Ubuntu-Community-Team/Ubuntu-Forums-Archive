---
title: "lost wireless internet upgrading to feisty"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by Pulka on 2007-05-08
I´m so frustrated. Lost 2 days, trying to put wireless internet working in my Edgy laptop. It was a nightmare. Finally did it. Decided to upgrade to feisty. Now i don´t have it anymore. Did the same procedures as before, but now they don´t work.
Instead of heaving a wlan0 in my connection name, it shows up a wlan0:avahi

Please, i need some help.

Here´s some information:

**lspci**

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:02.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller


**ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:C0:9F:85:53:31  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:6 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:716 (716.0 b)  TX bytes:716 (716.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0E:9B:A3:E6:CF  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:26 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:e0209000-e0209800 

wlan0:ava Link encap:Ethernet  HWaddr 00:0E:9B:A3:E6:CF  
          inet addr:169.254.10.209  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Memory:e0209000-e0209800 


**iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate=1 Mb/s   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0/100  Signal level:56/154  Noise level:160/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



**iwlist wlan0 scan**

wlan0     No scan results


**ndiswrapper -l**

neti2220 : driver installed
        device (17FE:2220) present


**ndiswrapper version: ** ndiswrapper-1.43

(Feisty installed me version 1.9, but i uninstalled it after some uncesseful trys. I also uninstalled network manager)

---

### Post by grahams on 2007-05-08
Looks like your wlan controller is claimed, but it's not find the network. Does your wireless LAN broadcast it's SSID. If not you may have the same issue others did. 

I got around it by opening the Network Admin tool, system >adminstration >network and manually adding the SSID name. wifiradar maybe also be a good tool for this.

I think others are still having issues with wlan on feisty and it may depend on your driver / controller.

---

### Post by Pulka on 2007-05-09
My essid is hidden. But i already have it named in wifi radar and in the network configurations. I had it before in edgy. Also one thing that i notice is that the light of the wireless card is off

---

### Post by Pulka on 2007-05-09
here´s another information:

[B]
tail /var/log/messages[/B]

May  9 10:32:07 ohg-laptop gconfd (root-6097): Exiting
May  9 10:36:16 ohg-laptop gconfd (root-6242): starting (version 2.18.0.1), pid 6242 user 'root'
May  9 10:36:16 ohg-laptop gconfd (root-6242): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
May  9 10:36:16 ohg-laptop gconfd (root-6242): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
May  9 10:36:16 ohg-laptop gconfd (root-6242): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
May  9 10:36:16 ohg-laptop gconfd (root-6242): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
May  9 10:36:16 ohg-laptop gconfd (root-6242): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
May  9 10:36:46 ohg-laptop gconfd (root-6242): GConf server is not in use, shutting down.
May  9 10:36:46 ohg-laptop gconfd (root-6242): Exiting
May  9 10:48:52 ohg-laptop -- MARK --

---

### Post by trapperjohn on 2007-05-09
Did you check, if Feisty loaded a module for your wireless card that conflicts with ndiswrapper (check 'dmesg' and 'lsmod')?

Did you try to manually start the network
sudo ifdown eth1
sudo ifup eth1

There seems to be a bug with feisty, some network interfaces aren't started correctly on boot.

---

### Post by grahams on 2007-05-09
To help diagnose the issue it may be worth taking your laptop to somewhere where it SSID is broadcast and see if you can attach to the network. If you still can't then it isn't the same issue as I had.

---

