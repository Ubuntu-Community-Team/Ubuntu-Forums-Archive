---
title: "[SOLVED] Wireless problems"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by Cilionelle on 2008-02-19
I have been going through kevdog's great introduction to networking in Ubuntu (muchas gracias!), but am still having some problems.  Please excuse the long post, but I have tried to include as much information as I can.  Any advice would be appreciated.

**Results of “lspci -v”**

```
03:02.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01) 
        Subsystem: Atheros Communications, Inc. EZ Connect g 802.11g 108Mbps Wireless PCI Adapter 
        Flags: bus master, medium devsel, latency 168, IRQ 21 
        Memory at dfbf0000 (32-bit, non-prefetchable) [size=64K] 
        Capabilities: <access denied> 

03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 04) 
        Subsystem: Dell Unknown device 01c4 
        Flags: bus master, medium devsel, latency 64, IRQ 18 
        Memory at dfbef000 (32-bit, non-prefetchable) [size=4K] 
        I/O ports at dcc0 [size=64] 
        Capabilities: <access denied> 
```

[B]
Results of “lshw -C network”[/B]

```
  *-network:0             
       description: Wireless interface 
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor 
       vendor: Atheros Communications, Inc. 
       physical id: 2 
       bus info: pci@0000:03:02.0 
       logical name: wifi0 
       version: 01 
       serial: 00:19:e0:88:30:4f 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g 
  *-network:1 
       description: Ethernet interface 
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller 
       vendor: Intel Corporation 
       physical id: 8 
       bus info: pci@0000:03:08.0 
       logical name: eth0 
       version: 04 
       serial: 00:16:76:58:26:eb 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes 
```

[B]
Results of “sudo dhclient -r ath0”[/B]

```
There is already a pid file /var/run/dhclient.pid with pid 134519120 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

wifi0: unknown hardware address type 801 
wifi0: unknown hardware address type 801 
Listening on LPF/ath0/00:19:e0:88:30:4f 
Sending on   LPF/ath0/00:19:e0:88:30:4f 
Sending on   Socket/fallback 

```

**Results of “sudo iwconfig wifi0 essid “wireless”**

```
Error for wireless request "Set ESSID" (8B1A) : 
    SET failed on device wifi0 ; Invalid argument. 
```

*No such results for ath0, seems to go through just fine.*

[B]
Results of “iwlist scan”[/B]

```
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

wifi0     Interface doesn't support scanning. 

ath0      Scan completed : 
          Cell 01 - Address: 00:60:64:05:8C:57 
                    ESSID:"wireless" 
                    Mode:Master 
                    Frequency:2.452 GHz (Channel 9) 
                    Quality=28/70  Signal level=-67 dBm  Noise level=-95 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:bcn_int=100 
          Cell 02 - Address: 00:0F:B5:55:E6:1E 
                    ESSID:"NETGEAR195" 
                    Mode:Master 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=220/70  Signal level=-131 dBm  Noise level=-95 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:bcn_int=100 
                    IE: WPA Version 1 
                        Group Cipher : WEP-40 
                        Pairwise Ciphers (1) : WEP-40 
                        Authentication Suites (1) : PSK
```


**Results of “ifconfig”**

```
ath0      Link encap:Ethernet  HWaddr 00:19:E0:88:30:4F  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 

ath0:avah Link encap:Ethernet  HWaddr 00:19:E0:88:30:4F  
          inet addr:169.254.5.189  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 

eth0      Link encap:Ethernet  HWaddr 00:16:76:58:26:EB  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:107 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:9612 (9.3 KB)  TX bytes:9612 (9.3 KB) 

wifi0     Link encap:UNSPEC  HWaddr 00-19-E0-88-30-4F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:9049 errors:0 dropped:0 overruns:0 frame:6260 
          TX packets:3145 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:199 
          RX bytes:980736 (957.7 KB)  TX bytes:157246 (153.5 KB) 
          Interrupt:21 
```


Conclusions: ath0 can find a wireless network (2 in fact), but the wireless adapter is wifi0.  How do I fix this so that the adapter finds the network?

---

### Post by Cilionelle on 2008-02-20
Bump.  Thanks for looking!

---

### Post by Junglizer on 2008-02-20
I'm going to help you in a randomly hap-hazard format sorry, just starting with pieces that I know offhand. 

**dhclient ath0**
```
There is already a pid file /var/run/dhclient.pid with pid 134519120 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

wifi0: unknown hardware address type 801 
wifi0: unknown hardware address type 801 
Listening on LPF/ath0/00:19:e0:88:30:4f 
Sending on   LPF/ath0/00:19:e0:88:30:4f 
Sending on   Socket/fallback
```

**There is already a pid file /var/run/dhclient.pid with pid 134519120 **
```
rm /var/run/dhclient.pid
```
dhclient had already run for the device and you need to delete the prior listing.

Also, what drivers are you using on this device? I see that it's an AR5212 (which in my opinion is one of the most reliable AR chipsets, especially in *nix).

---

### Post by Cilionelle on 2008-02-20
The driver Ubuntu is using is "ath_pci".  I don't know if that's the right one, and I'm not sure how to fix it if it's not.  The other thing that the Hardware Manager (is that right?) says is that although the manufacturer is correct, the WLAN interfacer says "Vendor Unknown" and "Device Unknown".  Is that normal?  The Networking Wireless Control Interface says the same.

Oh, and how do I go about deleting the prior entry?

---

### Post by Cilionelle on 2008-02-20
Bumpity!

---

### Post by Cilionelle on 2008-02-20
Bump it on up, y'all!  My thanks for looking, my official "Thanks" available for helping...

---

### Post by wirelessmonkey on 2008-02-20
wifi0 is your control interface, not actually the device, ath0.

the output of ~$: iwconfig 

would be mildly helpful.

then ~$: sudo ifconfig ath0 down
               sudo ifconfig ath0 up

What sort of encryption does the network you are trying to get on use?  You must first associate with the network, then provide the key, then ask for an address.  

Your wireless adapter is being loaded properly. Does network manager not show it?

---

### Post by freelinuxhelp on 2008-02-20
Don't know if it will help much, but here is the applicable info on my system.
sudo lspci -v
```
05:0a.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
        Subsystem: D-Link System Inc Unknown device 3a1b
        Flags: bus master, medium devsel, latency 168, IRQ 21
        Memory at e8410000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2
```

sudo ifconfig -a
```
ath0      Link encap:Ethernet  HWaddr 00:19:5B:78:1D:99  
          inet addr:192.168.1.60  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:5bff:fe78:1d99/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4741320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3138565 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2160573931 (2.0 GB)  TX bytes:623182279 (594.3 MB)

eth0      Link encap:Ethernet  HWaddr 00:0F:20:73:B7:09  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14335689 (13.6 MB)  TX bytes:14335689 (13.6 MB)

wifi0     Link encap:UNSPEC  HWaddr 00-19-5B-78-1D-99-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8460735 errors:0 dropped:0 overruns:0 frame:176017
          TX packets:3187178 errors:42 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:2880715961 (2.6 GB)  TX bytes:745570934 (711.0 MB)
          Interrupt:21 
```


sudo iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:14:BF:44:64:ED   
          Bit Rate:48 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:D6E2-D717-195D-1501-925E-8561-FA01-8CE6   Security mode:restricted
          Power Management:off
          Link Quality=33/70  Signal level=-61 dBm  Noise level=-94 dBm
          Rx invalid nwid:141  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by Cilionelle on 2008-02-20
> **wirelessmonkey said:**
> wifi0 is your control interface, not actually the device, ath0.

the output of ~$: iwconfig 

would be mildly helpful.

```
tom@satris:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wifi0     no wireless extensions. 

ath0      IEEE 802.11g  ESSID:"wireless"  Nickname:"" 
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm 
          Rx invalid nwid:218  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
```

> **wirelessmonkey said:**
> then ~$: sudo ifconfig ath0 down
               sudo ifconfig ath0 up

At &#8220;sudo ifconfig ath0 down&#8221; and then &#8220;sudo ifconfig ath0 up&#8221;, nothing appeared to happen (which I guess means it's all working well!).

> **wirelessmonkey said:**
> What sort of encryption does the network you are trying to get on use?  You must first associate with the network, then provide the key, then ask for an address.  

Your wireless adapter is being loaded properly. Does network manager not show it?

WEP encryption is being used; how do I do the things you have suggested?   Looking at the Network Tools, I see lo, eth0, wifi0, ath0 and ath0:avahi.  When I try to click Configure, I get a &#8220;This interface doesn't exist&#8221; message.  ath0, ath0:avahi and wifi0 are all called Unknown Interface in the list.  ath0:avahi gives an IP address, and wifi0 is the only one with packets flowing freely (but no IP or other settings).

Hope that helps.  Cheers!

---

### Post by Cilionelle on 2008-02-21
My goodness that was simple when I sat down and looked at it.  Junglizer had the right of it.  The old entry (wherever that came from) was disrupting the process.  I copied it to a backup file, redid the process and now I am typing this to you from Ubuntu!  Woohoo!  So, thanks to all for your patience!

---

