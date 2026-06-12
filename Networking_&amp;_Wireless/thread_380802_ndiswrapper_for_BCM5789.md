---
title: "ndiswrapper for BCM5789?"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by philipho on 2007-03-10
Hi all,

I installed Ubuntu a few days ago. Now i am hoping i can get my wireless up. My laptop is an Acer  
Aspire 5593 and my Ethernet controller information is as follows:

Ethernet controler: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 21)

However, i have been searching the forums but unable to find a ndiswrapper driver that is compatible with BCM5789. The following link only list BCM4306 and 4310 that is compatible with  
ndiswrapper.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)

I am new to Linux and rather confused here, help please.

---

### Post by teaker1s on 2007-03-10
ndiswrapper is for wireless cards, you need an ethernet driver possibly, though this broadcom page seems to indicate in kernel

[http://www.broadcom.com/support/ethernet_nic/faq_drivers.php#tg3]("http://www.broadcom.com/support/ethernet_nic/faq_drivers.php#tg3")

synaptic shows this source avaliable
bcm5700-source
module source for Broadcom's bcm5700 ethernet driver

---

### Post by philipho on 2007-03-10
I found out that the Broadcom bcm5789 uses the tg3 driver... I have downloaded the driver. However, i dont know how to go about installing it. Help please.

---

### Post by teaker1s on 2007-03-10
I'm guessing you downloaded the source code?

[https://help.ubuntu.com/community/CompilingSoftware]("https://help.ubuntu.com/community/CompilingSoftware")

[https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo")

---

### Post by philipho on 2007-03-10
Hi teaker1s, thanks for the help.

I extracted the file and and built it.
However, when i tried to load it, it gave access denied errors.

Anyway, i looked into the directory lib/modules/2.6.17-11-generic/kernel/drivers/net/ , i can see tg3.ko in that directory, does that mean the tg3 driver is already preinstalled? Below are some results:

**iwconfig eth1**

eth1      unassociated  ESSID:"Silver-Silent"  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1355   Missed beacon:0
[B]
sudo ifconfig eth1 up
sudo dhclient eth1[/B]

There is already a pid file /var/run/dhclient.pid with pid 5683
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:6e:a9:e5
Sending on   LPF/eth1/00:13:02:6e:a9:e5
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping


I can also see wireless connections under administration -> networking, however, it says it is not configured.

---

### Post by philipho on 2007-03-10
lol... i got it to work

just have to disable my eth0 =)

---

### Post by teaker1s on 2007-03-10
result

---

