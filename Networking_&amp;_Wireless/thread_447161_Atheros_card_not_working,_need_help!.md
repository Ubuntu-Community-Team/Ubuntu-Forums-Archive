---
title: "Atheros card not working, need help!"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by taishi28012 on 2007-05-17
I am having trouble getting wireless to work on my new laptop.  I have tried a few madwifi guides with no success and I have done a few other tricks but nothing seems to do it.  Please help me if you can.  Any advice is appreciated. 

Here is some info:

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

lspci:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

If you need any other info just tell me how to get it and ill deliver.  Thanks in advance!

---

### Post by ravenon on 2007-05-17
Do you have linux-restricted-modules installed? That is the only way I have ever had an Atheros card work.

---

### Post by dustigroove on 2007-05-17
[FONT=Arial][SIZE=2][COLOR=Black]Hey taishi28012 - what is your laptop make/model?

Cheers,

[/COLOR][/SIZE][/FONT]

---

### Post by dodd on 2007-05-18
Hi, I have same problem. More info:
[LIST]
[*]Card is Atheros AR5007EG
[*]lspci reports: 02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
[*]Laptop is Acer Asprire 5102AWLMi
[*]Ubuntu is 7.04 amd64
[*]restricted drivers are loaded, i can see ath_pci in lsmod
[*]I dont see card in ifconfig -a
[*]I have tried ndiswrapper too, but without luck.
[/LIST]

---

### Post by Gaerrent on 2007-05-19
I have the same provblem with an acer travelmate 2493.
the atheros tag under my computer says:Atheros AR5BXB63

in lsmod:
ath_pci                97312  0 
wlan                  204484  1 ath_pci
ath_hal               192592  1 ath_pci

dmesg | less:
[   15.288000] ath_pci: 0.9.4.5 (0.9.3)
[   15.120000] ath_hal: module license 'Proprietary' taints kernel.
[   15.120000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413,
 RF5413)
[   15.412000] wifi%d: unable to attach hardware: 'Hardware revision not supporte
d' (HAL status 13)

atheros hardware access layer is ticked in proprietary drivers

I have tried to install drivers via ndiswrapper and have tried both wicd and network manager.
I don know if all this info is usefull to get som help (Im a total noob)

---

### Post by dustigroove on 2007-05-20
[FONT=Arial][SIZE=2][COLOR=Black]Hi Gaerrent, please see [this thread]("http://ubuntuforums.org/showthread.php?p=2688436#post2688436") and see if either the guide for ndiswrapper or stchman's  madwifi guide help you out.

Cheers,

[/COLOR][/SIZE][/FONT]

---

### Post by Gaerrent on 2007-05-20
I tried yor guide dustigroove, but in the end I got this result:

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:d4:cf:47:d1
Sending on   LPF/eth0/00:16:d4:cf:47:d1
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:d4:cf:47:d1
Sending on   LPF/eth0/00:16:d4:cf:47:d1
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

---

### Post by fishdude21 on 2007-05-27
I have the same model card...the Aetheros AR5007EG.  I know ndiswrapper does not support this card.  However, linux doesnt even see the wireless card as an option to connect to the internet.  Is this normal or am i suppose to at least see the wireless card and it just not work?  I am connected right now through a lan line, which kind of defeats the purpose of a lapotp...

---

