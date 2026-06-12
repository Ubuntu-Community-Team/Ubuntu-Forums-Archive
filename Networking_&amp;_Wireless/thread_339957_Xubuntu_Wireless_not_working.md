---
title: "Xubuntu Wireless not working"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by Real Newbie on 2007-01-16
I posted this on the Absolute Beginner Talk forum yesterday and have not heard anything. It may be the wrong place. I am reposting here to see if anyone can help.

Greetings All,

I am setting up an old laptop that I used in Grad school for my 13 year old. He needs to browse the internet and do light word processing for school.

The laptop is an old Gateway Solo 2300, 150 Pentium MMX, 160 MB RAM, 20 GB HD. The wireless card is a Proxim 8480-WD. I loaded Ubuntu and it was just too much for the old machine. I tried DSL and I couldn't get my USB or wireless to work. Puppy warned that they did not do wireless well and that turned out to be true. I tried MEPIS and that auto detected everything well except for the wireless card. I tried for several weeks to get it to work and have officially given up. I have Ubuntu on an old Intel Nightshade server and am having fun playing with it so I decided to try Xbuntu on the old laptop. It took 4 install attempts to get it right. I had to fiddle with it awhile to get the screen setting close to right. Now it is time to tackle the wireless card. I have the following info.



```
kelly@xbuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 430TX - 82439TX MTXC (rev 01)
0000:00:01.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
0000:00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:01.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:01.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
0000:00:02.0 VGA compatible controller: Neomagic Corporation NM2093 [MagicGraph 128ZV] (rev 02)
0000:00:0a.0 CardBus bridge: Cirrus Logic PD 6832 PCMCIA/CardBus Ctrlr (rev c1)
0000:00:0a.1 CardBus bridge: Cirrus Logic PD 6832 PCMCIA/CardBus Ctrlr (rev c1)
0000:01:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
kelly@xbuntu:~$ iwconfig
lo        no wireless extensions.

ath0      IEEE 802.11  ESSID:"linksys"
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

kelly@xbuntu:~$ ifup ath0
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
kelly@xbuntu:~$
```

I see one problem right off the bat. I have a Linksys B wireless router. It is on channel 6 which is 2.442 GHz not 2.452. This was all of the same "stuff" that I was getting with MEPIS. Even after I changed the frequency, I still could not connect.

Questions
1)How do I change the frequency in Xbuntu?
2)Does anything stand out as wrong except for the frequency?

I am a real noob and am just having a little fun learning LINUX, so please make any suggestions as basic and step by step and complete as possible.

Thanks in advance for any and all help.

Noob

---

### Post by spd106 on 2007-01-16
Can I first ask which version of Xubuntu are using? They use different drivers for atheros based cards. It looks like you have 6.06 or 6.06.1. Also are you using WEP or WPA encryption?

From the output you got, your card does't appear to have found an AP to associate with, can you try scanning? Enter **sudo iwlist ath0 scan** at a terminal. It should produce a list of local APs.

Your ifup command failed because it needed root privileges, try **sudo ifup ath0**

---

### Post by Real Newbie on 2007-01-17
I believe I used the 6.06.1 alt iso to install. I am not using any type of encryption.

Thanks for the reply. I will try this tonight and post results.

Thanks so much for the help.

Noob

---

### Post by deejaylinux on 2007-01-17
It seems like no configuration is available for your wireless card.

Please read some of the howtos that you can get in sites like: 

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")
[http://ubuntuguide.org/]("http://ubuntuguide.org/")
[https://help.ubuntu.com/]("https://help.ubuntu.com/")

Hope this helps you.

Good like my friend!

---

### Post by Real Newbie on 2007-01-17
I tried the following

```
kelly@xbuntu:~$ sudo ifup ath0
ifup: interface ath0 already configured
kelly@xbuntu:~$ sudo iwlist ath0 scan
ath0      Failed to read scan data : Resource temporarily unavailable
```

Why would it fail to read the scan?

Thanks for any help.
Noob

---

### Post by Real Newbie on 2007-01-18
The mystery deepens,

I followed some advice from one of the links that I received (thx deejaylinux) and found something interesting.

> kelly@xbuntu:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:20:A6:4F:98:59
          inet6 addr: fe80::220:a6ff:fe4f:9859/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:caac0000-caad0000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15744 (15.3 KiB)  TX bytes:15744 (15.3 KiB)

Then

```
kelly@xbuntu:~$ sudo ifdown ath0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ath0/00:20:a6:4f:98:59
Sending on   LPF/ath0/00:20:a6:4f:98:59
Sending on   Socket/fallback
kelly@xbuntu:~$ sudo ifup wanlo
Ignoring unknown interface wanlo=wanlo.
kelly@xbuntu:~$ sudo ifup ath0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ath0/00:20:a6:4f:98:59
Sending on   LPF/ath0/00:20:a6:4f:98:59
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Then

```
kelly@xbuntu:~$ iwconfig ath0 mode managed
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Operation not permitted.
kelly@xbuntu:~$ iwconfig ath0 mode managediwconfig
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Operation not permitted.
```

I could not seem to set the managed mode

```
kelly@xbuntu:~$ iwconfig
lo        no wireless extensions.

ath0      IEEE 802.11  ESSID:"linksys"
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

In the above the frequency is 2.457 GHz

```
kelly@xbuntu:~$ iwconfig
lo        no wireless extensions.

ath0      IEEE 802.11  ESSID:"linksys"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

Now the frequency is 2.412

```
kelly@xbuntu:~$ iwconfig
lo        no wireless extensions.

ath0      IEEE 802.11  ESSID:"linksys"
          Mode:Managed  Frequency:5.805 GHz  Access Point: Not-Associated
          Bit Rate:6 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

Now it is 5.805-which is not even available on my wireless router. The router is set to Channel 6   2.442.GHz 
1)Why is the card jumping all over the place
2)It says > No working leases in persistent database - sleeping what does that mean? How do I fix it?

Sorry for the long post.

Any and all help is appreciated,
Noob

---

### Post by spd106 on 2007-01-19
You should be running most of these commands as root, i.e. prefix sudo. Then you will get more accurate information.

I don't like having to suggest this, but can you upgrade to Edgy (6.10)? The thing is that is has a newer version of madwifi, the atheros driver for your card. I believe it is more likely to work.

---

### Post by Real Newbie on 2007-01-19
I could upgrade to edgy, but I understand that it is a little unstable. I am new to LINUX and value the stability of 6.06.1.

Maybe the better question to ask is what cards do work out of the box? I thought the Atheros cards were supposed to work great. I have a Wireless G USB device. Should I try to install that?

Thx,
Noob

---

### Post by Real Newbie on 2007-01-19
One additional question

If you look at the result

```
kelly@xbuntu:~$ sudo ifup ath0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ath0/00:20:a6:4f:98:59
Sending on   LPF/ath0/00:20:a6:4f:98:59
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Xbuntu is listening on 255.255.255.255 however my subnet mask is 255.255.255.0. Is this significant? If so, how do I fix it?

Thanks for any help,
Noob

---

### Post by spd106 on 2007-01-19
No, this is the broadcast address for all networks, it's completely normal. 

Maybe you could download the latest madwifi driver from [http://madwifi.org](http://madwifi.org), You will need the build-essentials package in order to compile it. You can follow [this guide]("https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi") in the wiki or [this one]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo") on the madwifi site.

---

### Post by Real Newbie on 2007-01-20
The computer that I need this on has no internet access. I downloaded the MadWiFi tarball on to the desktop. Can anyone tell what to do next?

Thx,
Noob

---

