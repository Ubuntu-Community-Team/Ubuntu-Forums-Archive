---
title: "Wireless getting on my nerves"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by 98GreenGT on 2007-09-04
the only thing in my way of switching fully to ubuntu would be the networking...i finally got my card recognized and I can get connected to my wireless network, but Im getting speeds that top out at about 10 kb/sec where if i boot to vista I can have speeds in excess of 1k+.  Ive tried some small tips that Ive already searched for but I just cant find anything that will help

here is what i got from iwconfig-

eth1      IEEE 802.11b/g  ESSID:"GET OFF MY LINKSYS"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:1C:10:08:75:8A   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=93/100  Signal level=-45 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:743  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
Any help is appreciated ;0

---

### Post by bmartin on 2007-09-05
You appear to be using the firmware, I had that problem with the firmware, too. Try using [ndiswrapper]("http://ubuntuforums.org/showthread.php?t=405990") instead.

---

### Post by 98GreenGT on 2007-09-05
Ok ive done all that...and now it wont even connect to my network.  Thing is..it will connect to a random network around me that has no security and it will work fine...fast speeds and everything, but now it is refusing to connect to mine even if i unsecure it

---

### Post by 98GreenGT on 2007-09-06
Also i just installed knetwork manager and when i connect to my network it stops at 57% (ip configuration started) then it hangs up and dies...

---

### Post by kevdog on 2007-09-06
ok, lets just do some debugging

can you post 
lshw -C network
modinfo ndiswrapper
iwlist scan

I want you to try this from command line -- assuming your interface is wlan0. make sure you have an unencrypted router/ no mac filtering

```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 0.0.0.0
sudo dhclient -r wlan0
sudo killall dhclient dhclient3
sudo rm /var/run/dhclient.pid
sudo ip route flush dev wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid <"your_essid_in_quotes">
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0
```

---

### Post by 98GreenGT on 2007-09-06
*-network               
       description: Wireless interface
       product: BCM4310 UART
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@01:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:3a:c0:82
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.47+Broadcom,10/12/2006, 4.100. latency=0 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:c3000000-c3003fff irq:21
-------------------------------------------------------------------------------------------
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
license:        GPL
version:        1.47
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     FA633DF63916E1784E6852C
depends:        usbcore
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)
-------------------------------------------------------------------------------------------------
 Cell 01 - Address: 00:1C:10:08:75:8A
                    ESSID:"GET OFF MY LINKSYS"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-20 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 02 - Address: 00:18:F8:6D:DA:A6
                    ESSID:"JiyaYash"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:6/100  Signal level:-92 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:18:F8:CC:1A:43
                    ESSID:"DesiPatriots"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 04 - Address: 00:18:F8:B7:50:A6
                    ESSID:"jetfairfax"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:18:39:4B:7B:41
                    ESSID:"linksys-dumfries"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 06 - Address: 00:13:10:EE:FF:17
                    ESSID:"WBK"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/100  Signal level:-93 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 07 - Address: 00:18:01:F0:88:EF
                    ESSID:"JZQX2"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:29/100  Signal level:-77 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 08 - Address: 00:18:39:D7:EA:DF
                    ESSID:"caglayan"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:1/100  Signal level:-95 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
----------------------------------------------------------------------------------

not noticing any difference using the code you gave me replacing it with eth1

---

### Post by 98GreenGT on 2007-09-06
oh and by the way..when i try to connect to my network..it will ask for my password..ill enter it, and it'll continue to pop up the box asking for the password like its wrong or something

---

### Post by kevdog on 2007-09-06
Not saying this is going to solve your problem, however ndiswrapper by default expects the wireless interface to be wlan0.  Im not sure if during your installation you issued the command
sudo ndiswrapper -m

But first look in /etc/modprobe.d/ndiswrapper and tell me what it says.

Also post your 
/etc/iftab

Which of those wireless networks are yours, and what happened when you typed those commands?

---

### Post by kevdog on 2007-09-06
Oh yea, you cant run wired and wireless at the same time unless they are on different subnets.  So you either need to bring down the wired interface and up the wireless interface, or reboot with the wired ethernet cord unplugged.

---

### Post by 98GreenGT on 2007-09-06
alias wlan0 ndiswrapper
------------
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:16:d3:97:4d:4f arp 1
eth1 mac 00:1a:73:3a:c0:82 arp 1

---

### Post by stchman on 2007-09-06
> **98GreenGT said:**
> the only thing in my way of switching fully to ubuntu would be the networking...i finally got my card recognized and I can get connected to my wireless network, but Im getting speeds that top out at about 10 kb/sec where if i boot to vista I can have speeds in excess of 1k+.  Ive tried some small tips that Ive already searched for but I just cant find anything that will help

here is what i got from iwconfig-

eth1      IEEE 802.11b/g  ESSID:"GET OFF MY LINKSYS"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:1C:10:08:75:8A   
          Bit Rate=11 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=93/100  Signal level=-45 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:743  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
Any help is appreciated ;0

Broadcom cards are not fully supported by Linux as of this date.  There are some workarounds but it seems that folks on the forum here have problems with them.  You can always go get an Intel 3945ABG as they are fully supported by Ubuntu.  I see them on ebay for around $20 shipped.

---

### Post by kevdog on 2007-09-06
In your /etc/iftab file, Im assuming the entry associated with eth1 is the MAC address of your wireless card.  

I checked your lshw -C network statement and have confirmed this fact.

What I would do, is to simply comment out the eth1 line, (add a # sign in front of the line).  This usually seems to work rather than changing eth1 to wlan0. (Dont ask me why).  I would do this and then reboot.

After a reboot, verify that wlan0 is assigned to your network card by checking lshw -C network and looking for the line that states logical name.

---

### Post by 98GreenGT on 2007-09-06
wlan0 is now assigned but it still isnt connecting to my network

Also its not connecting to ANY wireless connection available now.  Its still asking me for my password over and over again on my network

---

### Post by kevdog on 2007-09-06
Ok, not a problem -- first disable WEP/WPA on the router, we need unencrypted

Next post 
lshw -C network
iwlist scan
modinfo ndiswrapper
ndiswrapper -l

No worries.

---

### Post by 98GreenGT on 2007-09-06
*-network               
       description: Wireless interface
       product: BCM4310 UART
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@01:00.0
       logical name: wlan0
       version: 01
       serial: 00:1a:73:3a:c0:82
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.47+Broadcom,10/12/2006, 4.100. latency=0 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:c3000000-c3003fff irq:21
------------------------------------

  Cell 01 - Address: 00:1C:10:08:75:8A
                    ESSID:"GET OFF MY LINKSYS"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:96/100  Signal level:-34 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:18:F8:CC:1A:43
                    ESSID:"DesiPatriots"
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
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
          Cell 03 - Address: 00:18:F8:B7:50:A6
                    ESSID:"jetfairfax"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:18:01:F0:88:EF
                    ESSID:"JZQX2"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
-----------------------------------------------------

filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
license:        GPL
version:        1.47
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     FA633DF63916E1784E6852C
depends:        usbcore
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)
-----------------------------------------------------------------
bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)
-------------------

It connected to a nearby unsecure network but when i restarted but hangs on the "getting IP Address" part for my network

---

### Post by kevdog on 2007-09-06
Which one of those networks are yours??
 
I hope its not secure at least for the moment

---

### Post by 98GreenGT on 2007-09-06
"GET OFF MY LINKSYS"  the first one

---

### Post by kevdog on 2007-09-06
First change the name of the router so it doesnt have any spaces in the name.  I know this might screw up your network but Ive seen problems with this.

Next type the following at the command line:

sudo ifconfig wlan0 down
sudo killall dhclient dhclient3
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "YOUR_ESSID_IN_QUOTES"
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

Tell me what you get after you change the essid name

---

### Post by 98GreenGT on 2007-09-06
Check back in on me tomorrow sometime and ill try to post up the results..im at the university now but everything is running smoothly here

---

### Post by Trash_Gordon on 2007-09-06
I had the same problem as you did. I don't think your problem is the network card, since you can connect to networks. Is your network "DesiPatriots"? Then your encryption is WPA1. You should try [http://ubuntuforums.org/showthread.php?t=318539]("http://ubuntuforums.org/showthread.php?t=318539"),
it's the __only__ thing that worked for me. It's not with a nice GUI, but it works. It would be nice if you could post
```
cat /var/log/messages | grep ndiswrapper
```
Please write the output in [CODE]-Tabs.

---

### Post by 98GreenGT on 2007-09-06
Well what can I say...I got back home after my 7-10 pm math class and booted up linux and well...it connected to my network fine lol.  It musta fixed itself with the mind of its own ;0

---

### Post by kevdog on 2007-09-06
That's probably what happened ;)

---

