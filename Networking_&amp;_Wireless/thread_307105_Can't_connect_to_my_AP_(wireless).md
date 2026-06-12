---
title: "Can't connect to my AP (wireless)"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by tee2 on 2006-11-26
This is what iwconfig eth1 looks like:

```

eth1      unassociated  ESSID:"Linksys_SES_38666"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:16:B6:A8:B3:F2   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

and here is what happens when i do dhclient eth1:

```
tee@tee-laptop:~$ sudo dhclient eth1
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:ce:e7:9e:a5
Sending on   LPF/eth1/00:13:ce:e7:9e:a5
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Any thought? And I do have dhcp enabled on my router.

---

### Post by tee2 on 2006-11-26
bump

---

### Post by shin on 2006-11-26
Have you tried static settings?

Also post your /etc/network/interfaces and 'iwlist scan' output

---

### Post by spd106 on 2006-11-26
Hi, you haven't been very clear about which card or chipset you have. Have a look here [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) and see if it is reported as working.

If you can't find it please post the output of **lspci** or if it's a usb device **lsusb**. If you have a Broadcom card then try installing ndiwrapper.

From the iwconfig output it looks like you have a driver problem.

---

### Post by MySweetTedy on 2006-11-27
hi i am trying for few days to configure everything on my wireless card and finally i got it working, in my university i got connected to the LRZ server, i had traffic with it and was able to open different sites. At home i have installed a wireless router, i can connect through Ethernet cable and everything works quite ok, also i got a xp laptop to have wireless Internet, all security and mac adr filters are off, my ath0 seems to work also fine <b>BUT</b> i cannot connect to neighter the router preferences via [http://192.168.0.1/](http://192.168.0.1/) nor to the Internet. here what i get from the iwlist scan:

```
ath0      Scan completed :
          Cell 01 - Address: 00:01:E3:D0:26:91
                    ESSID:""
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=7/94  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f0101000dff7f
          Cell 02 - Address: 00:0C:F6:21:7B:33
                    ESSID:"Sitecom"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/94  Signal level=-40 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:15:AF:08:00:84
                    ESSID:"Powerserver - X6800"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=13/94  Signal level=-82 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  


```
the network i want to connect to ¨sitecom¨
any help will be usefull, i tried 2 wireless clients wifi-radar and wireless assistant

---

