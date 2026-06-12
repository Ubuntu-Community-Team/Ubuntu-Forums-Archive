---
title: "Help Wireless Issues"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by RKNeff on 2008-04-09
You guys have probably heard this before but i have run into a snag. I am running Gutsy on an Acer Travelmate 2300 and almost everything works out really well. My one problem is the wireless. I have installed the windows driver using ndiswrapper.

my current wlan0 portion of the /etc/network/interfaces reads

auto wlan0
iface wlan0 inet static
wireless-essid Neff's Network
address 192.168.0.5
netmask 255.255.255.0
gateway 192.168.0.1
wireless-mode Managed
wireless-keymode open
wireless-key XXXXXXXXXX

I've been going through these forums for the last couple of days and I can get the wireless to see what networks are out there, but I can't seem to get into the one i need to.

Any help would be greatly appreciated.

---

### Post by Belak on 2008-04-09
can you post the outputs of:
iwconfig
and
iwlist scanning

Thanks,
Belak

---

### Post by RKNeff on 2008-04-10
Sure, here goes

iwconfig:

lo          no wireless extensions
eth0     no wireless extensions
wlan0   802.11g  ESSID:"Neff's Network"
            Mode:Managed   Frequency:2.412 GHz   Access Point: 00:09:5B:CD:91:74
             Bit Rate=54Mb/s
             RTS thr=2347 B    Fragment thr=2346 B
             Power Management:off
             Link Quality:95/100   Signal Level:-35dBm   Noise Level:-96dBm
             Rx invalid nwid:0   Rx invalid crypt:0   Rx invalid frag:0
             Tx excessive retries:0   Invalid misc:0   Missed beacon:0


And iwlist scanning (my network only):

lo           Interface doesn't support scanning
eth0      Interface doesn't support scanning

wlan0    scan completed :
      
              Cell 06 - Address:  00:09:5B:CD:91:74
                            ESSID: "Neff's Network"
                            Protocol:  IEEE  802.11g
                            Mode:  Managed
                            Frequency:  2.412 GHz  (Channel 1)
                            Quality 89/100    Signal Level:-39dBm      Noise Level:-96dBm
                            Encryption key:  on
                            Bit Rates:  1Mb/s;  2Mb/s;  5.5Mb/s;  11Mb/s;  6Mb/s
                                              9Mb/s;  12Mb/s;  18Mb/s;  24Mb/s;  36Mb/s
                                              48Mb/s;  54Mb/s
                            Extra:  bcn_int=100
                            Extra: atim=100

---

### Post by Belak on 2008-04-10
Ah... sorry... not iwconfig...
lshw -C network

This will say if your driver is working...

I like this guide:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

I know it's not what your looking for, but if you run into a snag there, it might help with your /etc/network/interfaces file

I have no idea.
Please post the output of that command, and if you run into any problems trying to connect from the command line.

So, if internet isn't working now try and run:
sudo dhclient wlan0

Sorry, that post was a jumble of information, but hopefully some of it will help.

---

### Post by RKNeff on 2008-04-10
alright then, here's lshw:

ryan@NorthernCountry:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network:0              
       description: Ethernet interface 
       product: BCM4401 100Base-T 
       vendor: Broadcom Corporation 
       physical id: 2 
       bus info: pci@0000:02:02.0 
       logical name: eth0 
       version: 01 
       serial: 00:c0:9f:66:2e:15 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=b44 driverversion=1.01 latency=64 module=b44 multicast=yes 
  *-network:1 
       description: Wireless interface 
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01) 
       vendor: Linksys, A Division of Cisco Systems 
       physical id: 4 
       bus info: pci@0000:02:04.0 
       logical name: wlan0 
       version: 00 
       serial: 00:0e:9b:68:e3:cb 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ndiswrapper+neti2220 driverversion=1.45+INPROCOMM,12/18/2003,1.17.1 latency=64 maxlatency=32 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

---

### Post by chili555 on 2008-04-10
I think one little snag may be that your ESSID contains a space: ```
ESSID: "Neff's Network"
``` I think your *interfaces* file should be amended to add quotes:```
wireless-essid **"**Neff's Network**"**
```Then restart networking```
sudo /etc/init.d/networking restart
``` and let us know.

---

### Post by RKNeff on 2008-04-10
alright, i changed the name of my network to not include spaces as well as changing the interfaces to include quaotes.

when i restarted my network this is the result that i got:

* reconfiguring network interfaces...
RTNETLINK answers:   No such process
SIOCDELRT:   No such process
Error for wireless request "Set Encode" (8B2A)  :
       SET failed on device wlan0  ;  Invalid argument.
Error for wireless request "Set Encode" (8B2A)  :
       SET failed on device wlan0  ;  Invalid argument.
Error for wireless request "Set ESSID" (8B1A)  :
       SET failed on device wlan0  ;  Invalid argument.


I'm lost, I can't figure what is set wrong in the interfaces file to cause these tree errors.

---

### Post by chili555 on 2008-04-10
> I can't figure what is set wrong in the interfaces fileLet's take a look at:```
cat /etc/network/interfaces
```as well as```
sudo iwlist wlan0 scan
```Thanks.

---

### Post by RKNeff on 2008-04-10
Okay here goes:

ryan@NorthernCountry:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5). 
# The loopback network interface
auto lo 
iface lo inet loopback 

# The primary network interface
auto wlan0 
iface wlan0 inet static 
  wireless-essid "Neffs-Network" 
  address 192.168.0.5 
  netmask 255.255.255.0 
  gateway 192.168.0.1 
  wireless-mode managed 
  wireless-keymode open 
  wireless-key 6C96687767 

ryan@NorthernCountry:~$ sudo iwlist wlan0 scan
wlan0     Scan completed : 
          Cell 01 - Address: 00:09:5B:CD:91:74 
                    ESSID:"Neffs-Network" 
                    Protocol:IEEE 802.11g 
                    Mode:Managed 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality:96/100  Signal level:-34 dBm  Noise level:-96 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 
          Cell 02 - Address: 00:18:F8:3C:FE:7A 
                    ESSID:"Charley1" 
                    Protocol:IEEE 802.11g 
                    Mode:Managed 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 
                              12 Mb/s; 48 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 
                    IE: WPA Version 1 
                        Group Cipher : WEP-40 
                        Pairwise Ciphers (1) : WEP-40 
                        Authentication Suites (1) : PSK 
          Cell 03 - Address: 00:1C:10:14:4D:76 
                    ESSID:"home1" 
                    Protocol:IEEE 802.11g 
                    Mode:Managed 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality:51/100  Signal level:-63 dBm  Noise level:-96 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 
                              12 Mb/s; 48 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 
                    IE: WPA Version 1 
                        Group Cipher : WEP-40 
                        Pairwise Ciphers (1) : WEP-40 
                        Authentication Suites (1) : PSK 
          Cell 04 - Address: 00:16:B6:CC:F0:9B 
                    ESSID:"linksys" 
                    Protocol:IEEE 802.11g 
                    Mode:Managed 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm 
                    Encryption key:off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 
                              12 Mb/s; 48 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0
          Cell 05 - Address: 00:12:17:CA:FB:24 
                    ESSID:"home" 
                    Protocol:IEEE 802.11g 
                    Mode:Managed 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 
                              12 Mb/s; 48 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 
                    IE: WPA Version 1 
                        Group Cipher : WEP-40 
                        Pairwise Ciphers (1) : WEP-40 
                        Authentication Suites (1) : PSK

---

### Post by RKNeff on 2008-04-10
Sorry for that list being so long I should have edited it to just my network.

---

### Post by chili555 on 2008-04-12
Please amend your *interfaces* file as follows:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto wlan0
iface wlan0 inet static
wireless-essid "Neffs-Network"
address 192.168.0.5
netmask 255.255.255.0
gateway 192.168.0.1
**#**wireless-mode managed
**#**wireless-keymode open
wireless-key 6C96687767
```The reason I'd like to try commenting out *managed* and *open* is because they are the default state. I also think *wireless-keymode* may be the incorrect terminology.

I run my network with shared key and so my *interfaces* file includes:```
wireless-key 6C96687767ABCD restricted
```After doing that, restart networking and let's see if any errors pop up:```
sudo /etc/init.d/networking restart
```If no errors occur, try pinging the gateway. If you get ping returns, you are golden!

---

