---
title: "Can't enable wireless device"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by paul la c on 2006-11-24
(new to Linux, BTW)

When I go to System Settings -> Network Settings, I can see my wireless card listed as disabled so I click enable device, a dialogue comes up saying that it is enabling the device, that disappears in a second and then the device is still disabled!

What is likely to be wrong?

FYI, I am running Edgy Kubuntu on a Lenovo N100 and it is a Broadcom 802.1g WLAN Mini Card that I am trying to use.

Thanks.

---

### Post by paul la c on 2006-11-24
*bumb*

update: iwconfig says:> lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.
and [i]ifup eth1 gives:> 
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:16:cf:89:a5:e1
Sending on   LPF/eth1/00:16:cf:89:a5:e1
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.Don't know if that's any help.

Thanks.

(P.S. and I know the network is not down)

---

### Post by guruofquality on 2006-11-24
do you accidentally have the wireless radio disabled? 
(on my dell i sometimes accidentally press fn+f2 and the wireless is disabled in hardware and spend hours trying to figure out what i did)

---

### Post by FrodoB on 2006-11-24
These bcm4311 devices have to be setup before they will work, have you done anything like setup the fwcutter or ndiswrapper to handle the wireless device?

---

### Post by paul la c on 2006-11-25
I haven't. Could you tell me what that means and how to do it (or link me to a tutorial)?

Thanks

---

### Post by FrodoB on 2006-11-25
Take a look at these instructions. One reporter says to definitely use ndiswrapper 1.28 rather than the new 1.29, I have not had time to investigate yet.

Here they are, and please report issues, as I was only able to go through these one time:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by paul la c on 2006-11-25
I don't think that's what I was looking for...> You should test that your device is applicable to this instruction using lspci:
Your output from lspci should contain a line very much like this: 
[quote]0X:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)[/quote]lspci says:> 03:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)

---

### Post by FrodoB on 2006-11-25
It is the same process, but your drivers will be different. Do a web search for someone's write up in the bcm4310 and you may find exact instructions.

---

### Post by huang earnie on 2006-12-13
> **guruofquality said:**
> do you accidentally have the wireless radio disabled? 
(on my dell i sometimes accidentally press fn+f2 and the wireless is disabled in hardware and spend hours trying to figure out what i did)


I'm in this boat - wireless card (Dell True Mobile 1300 WLAN Mini-PCI Card) is disabled in hardware.  However, fn-f2 isn't working to get it powered on.  Any alternative methods you know of?

---

### Post by FrodoB on 2006-12-13
For you wireless switch problem, possibly:

[http://sourceforge.net/projects/rfswitch/](http://sourceforge.net/projects/rfswitch/)

---

