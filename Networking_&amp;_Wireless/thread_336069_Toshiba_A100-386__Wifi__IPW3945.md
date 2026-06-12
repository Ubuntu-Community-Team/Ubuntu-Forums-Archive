---
title: "Toshiba A100-386 / Wifi / IPW3945"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by LeSmurf on 2007-01-11
Hi everyone,

I am using Ubuntu 6.10 on a Toshiba laptop. Everything is ok, but I am unable to configure the wireless. No pb at home, I only have to plug a wire. But next week, I have a professionnal travel for 3 months. I would like to use the Wifi connexion of hotels. 
The Wifi connexion works under windows. So, the hardware is fine. If I can't configure it under Linux, I would be very desappointed to use Windows on my Laptop for 3 months:-? 

My Wifi card is supposed to work immediatly : Intel IPW3945

What I did to fix this problem : 
1) I tried the normal procedure : to connect by using the Network menu of Gnome. But I don't see any wireless network like mine.

2) I installed Network-manager (0.6.3). Nice utility, my laptop is able to detect the wireless network around. However, I am unable to connect to my Wifi router.

Here is the logs : 

> Code:

syslog
---------------------------------------
Jan 10 20:54:52 laptop NetworkManager: <information>^IActivation (eth1) New wireless user key for network 'freebox_f' received. 
Jan 10 20:54:52 laptop NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 10 20:54:52 laptop NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) started... 
Jan 10 20:54:52 laptop NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Jan 10 20:54:52 laptop NetworkManager: <information>^IActivation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Jan 10 20:54:52 laptop NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) starting... 
Jan 10 20:54:52 laptop NetworkManager: <information>^IActivation (eth1/wireless): access point 'freebox_f' is encrypted, and a key exists.  No new key needed. 
Jan 10 20:54:53 laptop NetworkManager: <WARNING>^I real_act_stage2_config (): Activation (eth1/wireless): couldn't connect to the supplicant.
Jan 10 20:54:53 laptop NetworkManager: <information>^IActivation (eth1) failure scheduled... 
Jan 10 20:54:53 laptop NetworkManager: <information>^IActivation (eth1) Stage 2 of 5 (Device Configure) complete. 
Jan 10 20:54:53 laptop NetworkManager: <information>^Iwpa_supplicant(6534): Debugging disabled with CONFIG_NO_STDOUT_DEBUG=y build time option. 
Jan 10 20:54:53 laptop NetworkManager: <information>^IActivation (eth1) failed for access point (freebox_f) 
Jan 10 20:54:53 laptop NetworkManager: <information>^IActivation (eth1) failed. 
Jan 10 20:54:53 laptop NetworkManager: <information>^IDeactivating device eth1.

If somebody can help me, it would be really appreciated!

---

### Post by LeSmurf on 2007-01-11
I tried this script : 

```
ifconfig eth1 up
sleep 1
iwlist eth1 scan
sleep 1
iwconfig eth1 essid freebox_f
sleep 1
iwconfig eth1 mode managed
sleep 1
iwconfig eth1 key my_key
sleep 1
dhclient eth1

```

Trace : 
```


eth1      Scan completed :
          Cell 01 - Address: 00:0E:9B:A2:EC:DD
                    ESSID:"WANADOO-8D51"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=31/100  Signal level=-90 dBm  Noise level=-90 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 712ms ago
          Cell 02 - Address: 00:16:41:4F:59:BB
                    ESSID:"Wanadoo_c929"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:10
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=33/100  Signal level=-89 dBm  Noise level=-89 dBm
                    Extra: Last beacon: 716ms ago
          Cell 03 - Address: 00:14:A4:71:D8:1F
                    ESSID:"WANADOO-99D0"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=35/100  Signal level=-88 dBm  Noise level=-88 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 800ms ago
          Cell 04 - Address: 2A:67:E3:45:7E:3C
                    ESSID:"freebox_f"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=31/100  Signal level=-53 dBm  Noise level=-90 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : TKIP CCMP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 800ms ago
          Cell 05 - Address: 00:14:A4:73:75:B8
                    ESSID:"WANADOO-F118"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=46/100  Signal level=-81 dBm  Noise level=-81 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 808ms ago
          Cell 06 - Address: 2A:67:E3:45:7E:3F
                    ESSID:"freephonie"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=80/100  Signal level=-54 dBm  Noise level=-54 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : 802.1X  
                    Extra: Last beacon: 804ms ago
          Cell 07 - Address: 00:11:24:0E:94:0F
                    ESSID:"Philou"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=30/100  Signal level=-91 dBm  Noise level=-91 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 748ms ago
          Cell 08 - Address: 00:14:A4:5B:A7:C9
                    ESSID:"WANADOO-1AF0"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=33/100  Signal level=-89 dBm  Noise level=-89 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 784ms ago

There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:18:de:78:79:82
Sending on   LPF/eth1/00:18:de:78:79:82
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```


Commande :  iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"freebox_f"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 2A:67:E3:45:7E:3C   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=78/100  Signal level=-55 dBm  Noise level=-56 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2541   Missed beacon:0

sit0      no wireless extensions.

```

If somebody has an idea...

---

### Post by LeSmurf on 2007-01-11
Breaknews : 

I loaded the Ubuntu Live CD 6.10. I installed Network-Manager.
And... all was ok!!!

I probably damaged the configurations files before, when I tried to resolve the problem.

How can I fix it?
- to reconfigure some config files?
- to purge the Wifi softwares and to install it agaib?

Thanks

---

