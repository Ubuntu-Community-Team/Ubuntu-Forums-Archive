---
title: "Intel Pro/BG2200 Wireless (BCM4318)"
date: 2008-05-07
forum: Networking &amp; Wireless
---

### Post by servous on 2008-05-07
I've been Googling and searching forums for information on how to get my wireless working a couple of weeks now, but with no luck.

I've tested both fw-cutter, ndiswrapper, compiled ndiswrapper myself and 8-10 different drivers with no success.

The hardware is a mini-pci Intel Pro/2200BG wireless (Broadcom 4318 chipset).

My Linux-skills are very limited, and everything I've tried out has been on guide-basis. A friend of mine managed to get this card working in Getsy using ndiswrapper, but no luck in Hardy.

Please let me know if you need more information on my system/hardware/configuration.

I'm desperate..! ;)

- Thanks in advance!

---

### Post by chili555 on 2008-05-07
> Intel Pro/2200BG wireless (Broadcom 4318 chipset)What lead you to that conclusion? I don't think, thankfully, that this has anything to do with Broadcom.* Please do, in a terminal:```
sudo lshw -C network
```Please show us the information relating to your wireless and we'll troubleshoot.


-------------------------
*BRCM: bad for investors, but worse for Linux.

---

### Post by servous on 2008-05-07
Here is what lshw returns:

```
*-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth1
       version: 02
       serial: 00:14:a4:32:66:3e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.24-16-generic latency=64 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
```

In Windows the drivers used are bcmwl5, so it should be a Broadcom chipset. But I'm no expert on these kind of things... :)

The card is listed in nm-applet and shown up in iwconfig, but I'm not able to scan with it using iwlist.

(I just tried out the old bcm43xx just to see if it works, so no ndiswrapper at the moment.)

I really appreciate you're taking the time to help me out with this one - I'm stuck ;)

---

### Post by chili555 on 2008-05-07
This is indeed a Broadcom, but I sincerely doubt that anything anywhere says this Broadcom is an IPW2200. Please tell me what you have tried so far and what has failed. Your *lshw* looks healthy. Before you do anything more, may I please see:```
iwconfig eth1
lsmod | grep bcm
lsmod | grep b43
lsmod | grep ndis
uname -r
```Some of these may pop back to a prompt with no output; that's fine, it simply means no module like that is loaded.

Thanks.

---

### Post by servous on 2008-05-08
```

iwconfig eth1
eth1      No such device

lsmod | grep bcm
bcm43xx               127720  0 
ieee80211softmac       30976  1 bcm43xx
ieee80211              35528  2 bcm43xx,ieee80211softmac

lsmod | grep b43

lsmod | grep ndis

uname -r
2.6.24-16-generic

```

One more thing, meanwhile I'm using a PCMCIA wireless (Atheros). I don't think this should interfere with the Broadcom card.

---

### Post by chili555 on 2008-05-08
> I'm using a PCMCIA wireless (Atheros). I don't think this should interfere with the Broadcom card.It would quite surprise me if you were, without serious re-configuration deep within the warp core, able to get two wireless cards going at once. That is, unless you are setting up an access point, which supposes your cards and their drivers support it; not all do.

Moreover, Network Manager usually will not allow two interfaces to connect with two IP addresses at once. 

When you yank out the PCMCIA card and reboot, can you connect? Your *lshw* looks healthy; like it should love to connect!

If it does not connect, please do:```
dmesg | grep eth1
```See if there are any clues as to why it didn't.

---

### Post by servous on 2008-05-08
*dmesg | grep eth1* return nothing, but *dmesg | grep wlan0* returns:

```
[  133.797541] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

*lshw* returns:
```
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
```

*iwconfig* resturn:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Which method do you think works best for me; b43, bcm43xx or ndiswrapper?

For ndiswrapper I've been following this guide: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) with no success, even though it seems like it works for everybody else...

---

### Post by chili555 on 2008-05-08
In post #3, your *lshw* said it was using bcm43xx. Now this post says it's using b43. Am I trying to hit a moving target?

Your *iwconfig* looks healthy as is. Please do not change anything until we try out what you have.
Please do:```
sudo iwlist wlan0 scan
```Learn the exact name of the ESSID you want to connect to. Find out if there is encryption; WPA, WEP or Klingon. Then do:```
sudo iwconfig wlan0 essid <ur_essid>
sudo iwconfig wlan0 key <any_encryption_here?>
sudo dhclient wlan0
```Did you connect?

---

### Post by servous on 2008-05-09
**I finally got it all working!** :)

I'm now online with my BCM4318 using b43.

The reason to why it didn't work is because the radio was disabled at boot time, and rfkill couldn't turn it on and neither could I using the hardware LED-trigger.

After three weeks of experimenting with ndiswrapper, fw-cutter, compilators and kernels I finally got it working - just by changing the digit "0" to "1" in the file **/proc/acpi/acer/wireless**. This was an Acer-laptop issue, and the wireless hardware did actually work from the beginning.

I cannot enable/disable the wireless with the LED-trigger, but that's no issue for me (and probably most users), since I want to allways have the wireless enabled.

Case closed.

**Edit**
I noticed that the wireless radio was disabled every time the computer boots up from power off (not when rebooting).

[This link](http://ubuntuforums.org/archive/index.php/t-140007.html) contains information on how to set up a script that turns the wireless on on every boot.

---

### Post by chili555 on 2008-05-09
Great news! Glad it's working. Thank you very much for posting the specific solution so the searchers can find it!

---

### Post by rafaellmartin on 2008-05-24
I believe I have a very similar problem, but mine doesnt happen on an Acer, but on a HP Compaq NX6120. Interface is a BG2200.

That file "Servous" mentioned doesnt exist for me...

**The detais of my problem are:**

 - Connection is already configured, with WPA;
 - The connection works sometimes, but if I power off, sometimes it doesn't come back again in the next power on;
 - I cant get the IP address already set at eth1 (never), but doing ifdown and ifup commands generally force the DCHP to work;
 - It's very annoying do ifdown / ifup everytime I boot, and it's worse when it doesnt work, like I show below.

Right now, I powered on/off the laptop 03 times, and the DHCP still doesnt get the IP. Had to boot my XP partition to post this message.

Posting some results of the commands indicated in this post:
[B]
rafael@rafael-laptop:~$ sudo lshw -C network[/B]

  *-network:0                    
description: Wireless interface      
product: PRO/Wireless 2200BG Network Connection
vendor: Intel Corporation
physical id: 4
bus info: pci@0000:02:04.0 
logical name: eth1
version: 05 
serial: 00:13:ce:de:39:b0
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq
firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no
maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated 

*-network:1
description: Ethernet interface
product: NetXtreme BCM5705M_2
Gigabit Ethernet
vendor: Broadcom Corporation
physical id: e
bus info: pci@0000:02:0e.0
logical name: eth0
version: 03
serial: 00:15:60:b5:47:a9
capacity: 1GB/s
width: 64 bits
clock: 66MHz
capabilities: pm vpd msi bus_master cap_list ethernet
physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation      
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5705-v3.24
latency=64 link=no mingnt=64 module=tg3 multicast=yes port=twisted pair
[B]
rafael@rafael-laptop:~$ lsmod | grep bcm
rafael@rafael-laptop:~$ lsmod | grep b43
rafael@rafael-laptop:~$ lsmod | grep ndis
rafael@rafael-laptop:~$ uname -r[/B]
2.6.24-16-generic
**rafael@rafael-laptop:~$ dmesg | grep eth1**
[B]
rafael@rafael-laptop:~$ iwconfig eth1[/B]
eth1      IEEE 802.11g  ESSID:"marcon"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:F8:DA:11:9C   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=71/100  Signal level=-56 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:22  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[B]
rafael@rafael-laptop:~$ sudo iwlist eth1 scan[/B]
eth1      Scan completed :
          Cell 01 - Address: 00:18:F8:DA:11:9C
                    ESSID:"marcon"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=33/100  Signal level=-53 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 124ms ago

          Cell 02 - Address: 00:1C:10:57:9E:C8
                    ESSID:"peberna"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=41/100  Signal level=-76 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 8248ms ago

Other cells I left off the post.

Some icons have been created without my will, sorry for that.

I'm a Linux Dummie, but did a lot of research over this problem (I may say 90% of my linux knowledge comes from researching about this issue).

If someone has a clue, please post. 

Thanks in advance.

---

### Post by rafaellmartin on 2008-05-24
Forgot to show what happens at the ifdown/ifup commands

**rafael@rafael-laptop:~$ sudo ifdown eth1**
There is already a pid file /var/run/dhclient.eth1.pid with pid 5582
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Listening on LPF/eth1/00:13:ce:de:39:b0
Sending on   LPF/eth1/00:13:ce:de:39:b0
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67

**rafael@rafael-laptop:~$ sudo ifup eth1**
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Listening on LPF/eth1/00:13:ce:de:39:b0
Sending on   LPF/eth1/00:13:ce:de:39:b0
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

