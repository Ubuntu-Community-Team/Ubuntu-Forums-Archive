---
title: "Can't get IP address/network connection"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by erikcw on 2007-08-21
Hi,

My desktop has 2 network cards, a wired and a wireless.  The wired works fine, but I can't get a connection with my wireless card.

I can see the card in ifconfig, but it won't connect.

> 
$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"compex"
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:80:48:29:1B:52
          Bit Rate=36 Mb/s   Sensitivity=-200 dBm
          RTS thr=2346 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:56/100  Signal level:-60 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

> 
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D4:E0:F1:68
          inet addr:192.168.15.101  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fee0:f168/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:257621 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194033 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:322786507 (307.8 MiB)  TX bytes:18815094 (17.9 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10770 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10770 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:312456 (305.1 KiB)  TX bytes:312456 (305.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:40:F4:DC:B2:1D
          inet6 addr: fe80::240:f4ff:fedc:b21d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:28108 (27.4 KiB)  TX bytes:9731 (9.5 KiB)
          Interrupt:16 Memory:fded0000-fdee0000


> 
erik@turbo:~$ lspci | grep Ethernet
02:04.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
02:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)
erik@turbo:~$ sudo ifup wlan0
ifup: interface wlan0 already configured
erik@turbo:~$            
erik@turbo:~$ dmesg | grep wlan0
[   23.042544] wlan0: ethernet device 00:40:f4:dc:b2:1d using NDIS driver: mrv8335, version: 0x3000036, NDIS version: 0x500, vendor: '', 11AB:1FAA.5.conf
[   23.042561] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   77.247562] wlan0: no IPv6 routers present
[45729.434475] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[45735.827589] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[45746.724200] wlan0: no IPv6 routers present
[45765.911109] wlan0: no IPv6 routers present
erik@turbo:~$                              



The networking icon on my gnome panel only gives me the options of "Wired Network", and "Manual Configuration" - not a list of SSIDs like my laptop.

Any ideas what I can try to mak ethis work?

Thanks!
Erik

---

### Post by spd106 on 2007-08-22
Try these commands```

ndiswrapper -v
```
and ```
sudo iwlist wlan0 scan
```
Do you have encryption enabled? If so, double check the key is correct.

---

### Post by erikcw on 2007-08-22
Here is what I get:

> 
erik@turbo:~$ ndiswrapper -v
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586
erik@turbo:~$ sudo iwlist wlan0 scan
Password:
wlan0     Scan completed :
          Cell 01 - Address: 00:16:B6:67:ED:4F
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:6/100  Signal level:-92 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:80:48:29:1B:52
                    ESSID:"compex"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:78/100  Signal level:-46 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:05:5D:FA:B1:B4
                    ESSID:"D-Link"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:14:6C:DD:19:C9
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

erik@turbo:~$       


I do have WEP encryption and, and the key is correct.  Does the info above give any clues?

Thanks!
Erik

---

### Post by spd106 on 2007-08-23
[QUOTE=erikcw]erik@turbo:~$ ndiswrapper -v
[COLOR="Red"]utils Error: no version specified![/COLOR]
driver version: 1.38
vermagic: 2.6.20-16-generic SMP mod_unload 586[/QUOTE]

This is the problem. IMHO it's a serious bug in Ubuntu at the moment, though it doesn't appear to be being taken seriously. The common way around it is to download the latest version of [ndiswrapper]("http://sourceforge.net/project/showfiles.php?group_id=93482") (currently v1.47) and build it from source. You will need the build-essential and kernel headers packages. The procedure isn't difficult and there are several guides around this forum and the Ubuntu wiki.

e.g. [http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689), just ignore the Broadcom parts and use your normal driver as before.

---

