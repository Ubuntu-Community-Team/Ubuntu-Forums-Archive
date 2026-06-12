---
title: "Wireless Confusion (Recognized just don't understand setup)"
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by aqualad on 2006-12-02
Okay, so I'm trying to get my brother's computer working with my D-Link 520 Wireless PCI card, but I'm having trouble.  It's just a 520, I don't see a + sign on it and I don't think it's one of the troublesome E1 series I've been hearing about because it gets recognized out of the box. The problem is that I can't get it to find the router.  I can't even get it to list using

```
iwlist scan
```

Because when I do it says either No Scan Results or Network_down

Here's my /etc/network/interfaces file:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet dhcp


iface wlan0 inet dhcp
wireless-essid linksys
wireless-key *************************

auto eth0

iface wifi0 inet dhcp
wireless-essid linksys
wireless-key **************************

```

And then when I try
```
ifup wlan0
```

I get:

```
root@austin:/home/aqualad# ifup wlan0
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Invalid argument.
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wlan0/00:00:00:00:00:00
Sending on   LPF/wlan0/00:00:00:00:00:00
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I've tried things like
```
iwconfig wlan0 essid linksys
```

and it always gives me the error about
 "Error for wireless request "Set ESSID" (8B2A) :
    SET failed on device wlan0 ; Invalid argument."

Yeah, I'm just completely unsure what to do, I've tried setting it up through the GUI a bunch of times and keep failing.  Ugh. Help please?

---

### Post by FrodoB on 2006-12-02
What are the outputs of:

lspci

iwconfig

---

### Post by aqualad on 2006-12-03
```
aqualad@austin:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0b.0 Class ffff: Gammagraphx, Inc. Unknown device 0000

```

and

```
aqualad@austin:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11-DS  Mode:Managed  
          
wlan0     IEEE 802.11-DS  Mode:Managed  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

---

### Post by FrodoB on 2006-12-03
OK, give me a dump of dmesg.

---

### Post by aqualad on 2006-12-03
```
[17179770.264000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17179770.268000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179770.272000] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179770.272000] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[17179770.272000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179770.272000] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[17179770.272000] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[17179770.272000] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[17179770.272000] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[17179770.272000] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[17179770.272000] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[17179770.272000] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[17179770.272000] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[17179770.272000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179770.276000] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179770.276000] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[17179770.276000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179770.276000] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[17179770.276000] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[17179770.276000] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[17179770.276000] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[17179770.276000] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[17179770.276000] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[17179770.276000] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[17179770.276000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17179770.284000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179770.284000] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179770.284000] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[17179770.284000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179770.284000] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[17179770.284000] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[17179770.288000] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[17179770.288000] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[17179770.288000] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[17179770.288000] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[17179770.288000] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[17179770.288000] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[17179770.288000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179770.288000] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179770.288000] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[17179770.288000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179770.288000] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[17179770.288000] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[17179770.292000] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[17179770.292000] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[17179770.292000] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[17179770.292000] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[17179770.292000] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[17179770.292000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17179770.296000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179770.296000] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179770.300000] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[17179770.300000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179770.300000] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[17179770.300000] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[17179770.300000] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[17179770.300000] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[17179770.300000] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[17179770.300000] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[17179770.300000] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[17179770.300000] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[17179770.304000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179770.304000] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179770.304000] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[17179770.304000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179770.304000] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[17179770.304000] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[17179770.304000] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[17179770.304000] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[17179770.304000] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[17179770.304000] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[17179770.304000] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[17179770.304000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17179770.312000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179770.312000] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179770.312000] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[17179770.312000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179770.312000] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[17179770.316000] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[17179770.316000] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[17179770.316000] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[17179770.316000] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[17179770.316000] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[17179770.316000] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[17179770.316000] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[17179770.316000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179770.316000] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179770.316000] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[17179770.320000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179770.320000] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[17179770.320000] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[17179770.320000] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[17179770.320000] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[17179770.320000] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[17179770.320000] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[17179770.320000] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[17179770.320000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17179774.212000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.212000] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179774.212000] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[17179774.212000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.212000] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[17179774.212000] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[17179774.212000] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[17179774.212000] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[17179774.212000] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[17179774.212000] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[17179774.212000] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[17179774.212000] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[17179774.212000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.212000] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179774.212000] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[17179774.212000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.212000] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[17179774.212000] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[17179774.212000] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[17179774.212000] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[17179774.212000] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[17179774.212000] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[17179774.212000] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[17179774.212000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17179774.220000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.220000] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179774.220000] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[17179774.220000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.220000] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[17179774.220000] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[17179774.220000] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[17179774.220000] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[17179774.220000] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[17179774.220000] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[17179774.220000] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[17179774.220000] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[17179774.220000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.220000] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179774.220000] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[17179774.220000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.220000] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[17179774.220000] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[17179774.220000] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[17179774.220000] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[17179774.220000] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[17179774.220000] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[17179774.220000] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[17179774.220000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17179774.228000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.228000] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179774.228000] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[17179774.228000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.228000] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[17179774.228000] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[17179774.228000] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[17179774.228000] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[17179774.228000] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[17179774.228000] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[17179774.228000] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[17179774.228000] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[17179774.228000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.228000] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179774.228000] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[17179774.228000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.228000] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[17179774.228000] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[17179774.228000] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[17179774.228000] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[17179774.228000] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[17179774.228000] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[17179774.228000] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[17179774.228000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17179774.236000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.236000] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179774.236000] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[17179774.236000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.236000] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[17179774.236000] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[17179774.236000] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[17179774.236000] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[17179774.236000] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[17179774.236000] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[17179774.236000] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[17179774.236000] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[17179774.236000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.236000] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179774.236000] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[17179774.236000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.236000] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[17179774.236000] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[17179774.236000] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[17179774.236000] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[17179774.236000] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[17179774.236000] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[17179774.236000] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[17179774.236000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17179774.244000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.244000] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179774.244000] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[17179774.244000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.244000] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[17179774.244000] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[17179774.244000] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[17179774.244000] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[17179774.244000] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[17179774.244000] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[17179774.244000] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[17179774.244000] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[17179774.244000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.244000] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179774.244000] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[17179774.244000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.244000] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[17179774.244000] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[17179774.244000] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[17179774.244000] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[17179774.244000] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[17179774.244000] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[17179774.244000] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[17179774.244000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17179774.252000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.252000] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179774.252000] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[17179774.252000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.252000] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[17179774.252000] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[17179774.252000] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[17179774.252000] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[17179774.252000] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[17179774.252000] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[17179774.252000] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[17179774.252000] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[17179774.252000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.252000] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179774.252000] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[17179774.252000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.252000] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[17179774.252000] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[17179774.252000] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[17179774.252000] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[17179774.252000] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[17179774.252000] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[17179774.252000] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[17179774.252000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17179774.260000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.260000] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179774.260000] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[17179774.260000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.260000] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[17179774.260000] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[17179774.260000] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[17179774.260000] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[17179774.260000] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[17179774.260000] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[17179774.260000] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[17179774.260000] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[17179774.260000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.260000] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179774.260000] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[17179774.260000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.260000] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[17179774.260000] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[17179774.260000] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[17179774.260000] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[17179774.260000] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[17179774.260000] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[17179774.260000] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[17179774.260000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17179774.396000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.396000] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179774.396000] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[17179774.396000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.396000] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[17179774.396000] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[17179774.396000] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[17179774.396000] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[17179774.396000] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[17179774.400000] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[17179774.400000] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[17179774.400000] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[17179774.400000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.400000] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179774.400000] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[17179774.400000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179774.400000] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[17179774.400000] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[17179774.400000] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[17179774.400000] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[17179774.400000] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[17179774.400000] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[17179774.404000] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[17179774.404000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17179803.336000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.336000] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179803.336000] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[17179803.336000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.336000] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[17179803.336000] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[17179803.336000] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[17179803.336000] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[17179803.336000] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[17179803.336000] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[17179803.336000] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[17179803.336000] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[17179803.336000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.336000] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179803.336000] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[17179803.336000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.336000] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[17179803.336000] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[17179803.336000] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[17179803.336000] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[17179803.336000] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[17179803.336000] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[17179803.336000] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[17179803.336000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17179803.340000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.340000] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179803.340000] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[17179803.340000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.340000] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[17179803.340000] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[17179803.340000] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[17179803.340000] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[17179803.340000] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[17179803.340000] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[17179803.340000] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[17179803.340000] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[17179803.340000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.340000] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179803.340000] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[17179803.340000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.340000] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[17179803.340000] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[17179803.340000] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[17179803.340000] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[17179803.340000] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[17179803.340000] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[17179803.340000] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[17179803.340000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17179803.344000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.344000] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179803.344000] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[17179803.344000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.344000] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[17179803.344000] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[17179803.344000] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[17179803.344000] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[17179803.344000] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[17179803.344000] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[17179803.344000] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[17179803.344000] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[17179803.344000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.344000] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179803.344000] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[17179803.344000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.344000] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[17179803.344000] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[17179803.344000] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[17179803.344000] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[17179803.344000] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[17179803.344000] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[17179803.344000] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[17179803.344000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17179803.352000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.352000] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179803.352000] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[17179803.352000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.352000] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[17179803.352000] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[17179803.352000] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[17179803.352000] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[17179803.352000] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[17179803.352000] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[17179803.352000] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[17179803.352000] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[17179803.352000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.352000] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179803.352000] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[17179803.352000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.352000] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[17179803.352000] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[17179803.352000] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[17179803.352000] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[17179803.352000] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[17179803.352000] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[17179803.352000] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[17179803.352000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17179803.356000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.356000] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179803.356000] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[17179803.356000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.356000] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[17179803.356000] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[17179803.356000] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[17179803.356000] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[17179803.356000] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[17179803.356000] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[17179803.356000] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[17179803.356000] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[17179803.356000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.356000] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179803.356000] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[17179803.356000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.356000] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[17179803.356000] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[17179803.356000] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[17179803.356000] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[17179803.356000] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[17179803.356000] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[17179803.356000] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[17179803.356000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17179803.408000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.408000] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179803.408000] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[17179803.408000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.408000] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[17179803.408000] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[17179803.408000] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[17179803.408000] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[17179803.408000] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[17179803.412000] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[17179803.412000] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[17179803.412000] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[17179803.412000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.412000] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179803.412000] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[17179803.412000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.412000] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[17179803.412000] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[17179803.412000] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[17179803.412000] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[17179803.412000] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[17179803.416000] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[17179803.416000] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[17179803.416000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17179803.420000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.420000] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179803.420000] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[17179803.420000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.424000] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[17179803.424000] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[17179803.424000] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[17179803.424000] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[17179803.424000] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[17179803.424000] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[17179803.424000] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[17179803.424000] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[17179803.424000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.424000] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[17179803.424000] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[17179803.424000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17179803.428000] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[17179803.428000] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[17179803.428000] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[17179803.428000] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[17179803.428000] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[17179803.428000] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[17179803.428000] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[17179803.428000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17179836.364000] ieee80211_crypt: registered algorithm 'WEP'
[17179836.396000] wifi0: cannot get RID fc28 (len=2) - no PRI f/w
[17179836.396000] Could not read current WEP flags.
[17179836.396000] wifi0: encryption setup failed
[17179836.396000] wlan0: set_encryption failed
[17179836.400000] wlan0: cannot set RID fc02 (len=34) - no PRI f/w
[17179836.440000] wlan0: could not set interface UP - no PRI f/w
[17179836.440000] wlan0: could not set interface UP - no PRI f/w
[17180076.436000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17180076.436000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17206757.460000] usb 4-2: USB disconnect, address 2
[17257745.072000] usb 4-2: new low speed USB device using uhci_hcd and address 3
[17257745.252000] usb 4-2: configuration #1 chosen from 1 choice
[17257745.276000] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /class/input/input3
[17257745.276000] input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.2-2
[17257812.520000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17257812.520000] wifi0: cannot get RID fdc1 (len=2) - no PRI f/w
[17257812.520000] wifi0: cannot get RID fd41 (len=34) - no PRI f/w
[17257812.520000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w
[17257812.520000] wifi0: cannot get RID fc06 (len=2) - no PRI f/w
[17257812.520000] wifi0: cannot get RID fd42 (len=6) - no PRI f/w
[17257812.520000] wifi0: cannot get RID fc0e (len=34) - no PRI f/w
[17257812.520000] wifi0: cannot get RID fc84 (len=2) - no PRI f/w
[17257812.520000] wifi0: cannot get RID fc83 (len=2) - no PRI f/w
[17257812.520000] wifi0: cannot get RID fc82 (len=2) - no PRI f/w
[17257812.520000] wifi0: cannot get RID fc09 (len=2) - no PRI f/w
[17257812.520000] wifi0: cannot get RID fd48 (len=2) - no PRI f/w
[17257812.520000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17257812.520000] wlan0: cannot get RID fdc1 (len=2) - no PRI f/w
[17257812.520000] wlan0: cannot get RID fd41 (len=34) - no PRI f/w
[17257812.520000] wlan0: cannot get RID fdc6 (len=12) - no PRI f/w
[17257812.520000] wlan0: cannot get RID fc06 (len=2) - no PRI f/w
[17257812.520000] wlan0: cannot get RID fd42 (len=6) - no PRI f/w
[17257812.520000] wlan0: cannot get RID fc0e (len=34) - no PRI f/w
[17257812.520000] wlan0: cannot get RID fc84 (len=2) - no PRI f/w
[17257812.524000] wlan0: cannot get RID fc83 (len=2) - no PRI f/w
[17257812.524000] wlan0: cannot get RID fc82 (len=2) - no PRI f/w
[17257812.524000] wlan0: cannot get RID fc09 (len=2) - no PRI f/w
[17257812.524000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17259999.168000] usb 4-2: USB disconnect, address 3

```

I didn't get it all, but yeah, I'm pretty sure that means I need Prism firmware doesn't it?  Can I use the PM to get it or is it a manual install?

---

### Post by FrodoB on 2006-12-03
I want to see the part where the the prism device driver is loaded, it must be just before this part.

---

### Post by aqualad on 2006-12-03
Okay, captured to a file, here it is:

```
[17179569.184000] Linux version 2.6.17-10-386 (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Fri Oct 13 18:41:40 UTC 2006 (Ubuntu 2.6.17-10.33-386)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[17179569.184000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001f6f0000 (usable)
[17179569.184000]  BIOS-e820: 000000001f6f0000 - 000000001f6ff000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001f6ff000 - 000000001f700000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001f700000 - 000000001f780000 (usable)
[17179569.184000]  BIOS-e820: 000000001f780000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 503MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f6630
[17179569.184000] On node 0 totalpages: 128896
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 124800 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6670
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1f6f8bf7
[17179569.184000] ACPI: FADT (v001 INTEL  NBGV     0x06040000 PTL  0x00000003) @ 0x1f6fef14
[17179569.184000] ACPI: MADT (v001 PTLTD  	 APIC   0x06040000  LTP 0x00000000) @ 0x1f6fef88
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1f6fefd8
[17179569.184000] ACPI: DSDT (v001  INTEL Brkdle_G 0x06040000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:1 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:df800000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1803.635 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.628000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.628000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.648000] Memory: 501776k/515584k available (1829k kernel code, 13188k reserved, 1038k data, 288k init, 0k highmem)
[17179571.648000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.728000] Calibrating delay using timer specific routine.. 3592.52 BogoMIPS (lpj=7185050)
[17179571.728000] Security Framework v1.0.0 initialized
[17179571.728000] SELinux:  Disabled at boot.
[17179571.728000] Mount-cache hash table entries: 512
[17179571.728000] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179571.728000] CPU: After vendor identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179571.728000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179571.728000] CPU: L2 cache: 128K
[17179571.728000] CPU: After all inits, caps: 3febfbff 00000000 00000000 00000080 00000000 00000000 00000000
[17179571.728000] CPU: Intel(R) Celeron(R) CPU 1.80GHz stepping 03
[17179571.728000] Checking 'hlt' instruction... OK.
[17179571.744000] SMP alternatives: switching to UP code
[17179571.744000] Freeing SMP alternatives: 0k freed
[17179571.744000] checking if image is initramfs... it is
[17179572.452000] Freeing initrd memory: 5182k freed
[17179572.452000] ACPI: Core revision 20060707
[17179572.452000] ACPI: Looking for DSDT ... not found!
[17179572.456000] ENABLING IO-APIC IRQs
[17179572.456000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179572.600000] NET: Registered protocol family 16
[17179572.600000] EISA bus registered
[17179572.600000] ACPI: bus type pci registered
[17179572.600000] PCI: PCI BIOS revision 2.10 entry at 0xfd99a, last bus=2
[17179572.600000] PCI: Using configuration type 1
[17179572.600000] Setting up standard PCI resources
[17179572.628000] ACPI: Interpreter enabled
[17179572.628000] ACPI: Using IOAPIC for interrupt routing
[17179572.632000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.632000] PCI: Probing PCI hardware (bus 00)
[17179572.632000] Boot video device is 0000:00:02.0
[17179572.632000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179572.632000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179572.632000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179572.632000] PCI: Transparent bridge - 0000:00:1e.0
[17179572.636000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.636000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SLOT._PRT]
[17179572.640000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[17179572.640000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[17179572.640000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[17179572.640000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[17179572.640000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179572.644000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179572.644000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179572.644000] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 7 9 10 11 12 14 15)
[17179572.648000] ACPI: Power Resource [FN01] (on)
[17179572.648000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.648000] pnp: PnP ACPI init
[17179572.676000] pnp: PnP ACPI: found 10 devices
[17179572.676000] PnPBIOS: Disabled by ACPI PNP
[17179572.676000] PCI: Using ACPI for IRQ routing
[17179572.676000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.680000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179572.680000] PCI: Bridge: 0000:00:1e.0
[17179572.680000]   IO window: 2000-2fff
[17179572.680000]   MEM window: e8100000-e81fffff
[17179572.680000]   PREFETCH window: f8000000-f80fffff
[17179572.680000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179572.680000] NET: Registered protocol family 2
[17179572.720000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179572.720000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179572.720000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[17179572.720000] TCP: Hash tables configured (established 16384 bind 8192)
[17179572.720000] TCP reno registered
[17179572.720000] Simple Boot Flag at 0x3b set to 0x1
[17179572.720000] * This chipset may have PM-Timer Bug.  Due to workarounds for a bug,
[17179572.720000] * this time source is slow. If you are sure your timer does not have
[17179572.720000] * this bug, please use "pmtmr_good" to disable the workaround
[17179572.720000] audit: initializing netlink socket (disabled)
[17179572.720000] audit(1165100798.720:1): initialized
[17179572.720000] VFS: Disk quotas dquot_6.5.1
[17179572.720000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.720000] Initializing Cryptographic API
[17179572.720000] io scheduler noop registered
[17179572.720000] io scheduler anticipatory registered
[17179572.720000] io scheduler deadline registered
[17179572.720000] io scheduler cfq registered (default)
[17179572.720000] isapnp: Scanning for PnP cards...
[17179573.076000] isapnp: No Plug & Play device found
[17179573.176000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179573.176000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.180000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.180000] mice: PS/2 mouse device common for all mice
[17179573.180000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.180000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.180000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.180000] PNP: PS/2 Controller [PNP0303:KBC0] at 0x60,0x64 irq 1
[17179573.180000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179573.192000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.192000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.192000] EISA: Probing bus 0 at eisa.0
[17179573.192000] Cannot allocate resource for EISA slot 1
[17179573.192000] Cannot allocate resource for EISA slot 2
[17179573.192000] EISA: Detected 0 cards.
[17179573.196000] TCP bic registered
[17179573.196000] NET: Registered protocol family 1
[17179573.196000] NET: Registered protocol family 8
[17179573.196000] NET: Registered protocol family 20
[17179573.196000] Using IPI Shortcut mode
[17179573.196000] ACPI: (supports S0 S1 S3 S4 S5)
[17179573.196000] Freeing unused kernel memory: 288k freed
[17179573.220000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.396000] Capability LSM initialized
[17179574.460000] ACPI: Transitioning device [FAN1] to D0
[17179574.460000] ACPI: Transitioning device [FAN1] to D0
[17179574.460000] ACPI: Fan [FAN1] (off)
[17179574.468000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179574.476000] ACPI: Thermal Zone [THRM] (-269 C)
[17179575.368000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[17179575.368000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179575.368000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 177
[17179575.368000] ICH4: chipset revision 1
[17179575.368000] ICH4: not 100% native mode: will probe irqs later
[17179575.368000]     ide0: BM-DMA at 0x1860-0x1867, BIOS settings: hda:DMA, hdb:pio
[17179575.368000]     ide1: BM-DMA at 0x1868-0x186f, BIOS settings: hdc:DMA, hdd:pio
[17179575.368000] Probing IDE interface ide0...
[17179575.664000] hda: Maxtor 6E040L0, ATA DISK drive
[17179576.336000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.344000] Probing IDE interface ide1...
[17179577.080000] hdc: Hewlett-Packard CD-Writer cd16f, ATAPI CD/DVD-ROM drive
[17179577.416000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.436000] hda: max request size: 128KiB
[17179577.444000] hda: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
[17179577.444000] hda: cache flushes supported
[17179577.444000]  hda: hda1 < hda5 > hda2 hda3
[17179577.488000] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179577.488000] Uniform CD-ROM driver Revision: 3.20
[17179577.816000] usbcore: registered new driver usbfs
[17179577.816000] usbcore: registered new driver hub
[17179577.816000] USB Universal Host Controller Interface driver v3.0
[17179577.816000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 185
[17179577.816000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179577.816000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179577.816000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179577.816000] uhci_hcd 0000:00:1d.0: irq 185, io base 0x00001800
[17179577.816000] usb usb1: configuration #1 chosen from 1 choice
[17179577.816000] hub 1-0:1.0: USB hub found
[17179577.816000] hub 1-0:1.0: 2 ports detected
[17179577.920000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 193
[17179577.920000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179577.920000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179577.920000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[17179577.920000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179577.920000] ehci_hcd 0000:00:1d.7: irq 193, io mem 0xe8080000
[17179577.924000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.924000] usb usb2: configuration #1 chosen from 1 choice
[17179577.924000] hub 2-0:1.0: USB hub found
[17179577.924000] hub 2-0:1.0: 6 ports detected
[17179578.044000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 201
[17179578.044000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179578.044000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179578.044000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[17179578.044000] uhci_hcd 0000:00:1d.1: irq 201, io base 0x00001820
[17179578.044000] usb usb3: configuration #1 chosen from 1 choice
[17179578.044000] hub 3-0:1.0: USB hub found
[17179578.044000] hub 3-0:1.0: 2 ports detected
[17179578.148000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 177
[17179578.148000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179578.148000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179578.148000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[17179578.148000] uhci_hcd 0000:00:1d.2: irq 177, io base 0x00001840
[17179578.148000] usb usb4: configuration #1 chosen from 1 choice
[17179578.148000] hub 4-0:1.0: USB hub found
[17179578.148000] hub 4-0:1.0: 2 ports detected
[17179578.356000] Attempting manual resume
[17179578.384000] kjournald starting.  Commit interval 5 seconds
[17179578.384000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.492000] usb 4-2: new low speed USB device using uhci_hcd and address 2
[17179578.672000] usb 4-2: configuration #1 chosen from 1 choice
[17179591.680000] parport: PnPBIOS parport detected.
[17179591.680000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179591.744000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179591.756000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179591.824000] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[17179592.268000] Linux agpgart interface v0.101 (c) Dave Jones
[17179592.276000] agpgart: Detected an Intel 845G Chipset.
[17179592.276000] agpgart: Detected 8060K stolen memory.
[17179592.292000] agpgart: AGP aperture is 128M @ 0xf0000000
[17179592.528000] hw_random: RNG not detected
[17179592.640000] Floppy drive(s): fd0 is 1.44M
[17179592.656000] FDC 0 is a post-1991 82077
[17179592.784000] Real Time Clock Driver v1.12ac
[17179592.864000] input: PC Speaker as /class/input/input1
[17179593.084000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 209
[17179593.084000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179593.400000] intel8x0_measure_ac97_clock: measured 53858 usecs
[17179593.400000] intel8x0: clocking to 48000
[17179594.164000] usbcore: registered new driver hiddev
[17179594.184000] prism2pci_init: prism2_pci.o: 0.2.5 Loaded
[17179594.184000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 193
[17179594.184000] A Prism2.5 PCI device found, phymem:0xf8000000, irq:193, mem:0xe0214000
[17179596.932000] hfa384x_corereset: corereset: Timed out waiting for cmd register.
[17179596.932000] prism2sta_probe_pci: prism2_pci: hfa384x_corereset() failed.
[17179596.952000] 8139too Fast Ethernet driver 0.9.27
[17179596.984000] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /class/input/input2
[17179596.984000] input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.2-2
[17179596.984000] usbcore: registered new driver usbhid
[17179596.984000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179597.056000] ACPI: PCI interrupt for device 0000:02:0b.0 disabled
[17179597.056000] prism2_pci: probe of 0000:02:0b.0 failed with error -5
[17179597.056000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 17 (level, low) -> IRQ 209
[17179597.056000] eth0: RealTek RTL8139 at 0xe0002000, 00:40:2b:27:58:fd, IRQ 209
[17179597.056000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179597.068000] ts: Compaq touchscreen protocol output
[17179597.080000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179597.132000] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17179597.132000] orinoco_pci 0.15rc3 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au> & Jean Tourrilhes <jt@hpl.hp.com>)
[17179597.132000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 193
[17179597.132000] orinoco_pci: Detected device 0000:02:0b.0, mem:0xf8000000-0xf8000fff, irq 193
[17179598.376000] orinoco_pci: Busy timeout
[17179598.376000] orinoco_pci: Initial reset failed
[17179598.376000] ACPI: PCI interrupt for device 0000:02:0b.0 disabled
[17179598.376000] orinoco_pci: probe of 0000:02:0b.0 failed with error -110
[17179598.412000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179598.636000] ieee80211_crypt: registered algorithm 'NULL'
[17179598.664000] hostap_pci: 0.4.4-kernel (Jouni Malinen <jkmaline@cc.hut.fi>)
[17179598.668000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 193
[17179598.668000] hostap_pci: Registered netdevice wifi0
[17179598.668000] wifi0: Original COR value: 0xa9
[17179598.672000] wifi0: COR sreset timeout
[17179598.688000] wifi0: __hfa384x_cmd_no_wait(6) - timeout - reg=0xdda9
[17179598.688000] hostap_pci: first command failed - assuming card does not have primary firmware
[17179599.188000] hostap_pci: assuming no Primary image in flash - card initialization not completed
[17179599.188000] wifi0: test Genesis mode with HCR 0x1f
[17179599.188000] wifi0: Original COR value: 0xa9
[17179599.188000] wifi0: COR sreset timeout
[17179599.220000] Readback test failed, HCR 0x1f write 00 e1 a1 ff read 00 ce a1 ce
[17179599.220000] wifi0: test Genesis mode with HCR 0x0f
[17179599.220000] wifi0: Original COR value: 0xa1
[17179599.224000] wifi0: COR sreset timeout
[17179599.252000] Readback test succeeded, HCR 0x0f
[17179599.284000] wifi0: Intersil Prism2.5 PCI: mem=0xf8000000, irq=193
[17179599.284000] wifi0: registered netdevice wlan0
[17179599.448000] NET: Registered protocol family 17
[17179599.468000] lp0: using parport0 (interrupt-driven).
[17179599.524000] Adding 498004k swap on /dev/hda5.  Priority:-1 extents:1 across:498004k
[17179599.656000] EXT3 FS on hda2, internal journal
[17179600.584000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179601.412000] NET: Registered protocol family 10
[17179601.412000] lo: Disabled Privacy Extensions
[17179601.412000] IPv6 over IPv4 tunneling driver
[17179602.552000] ACPI: Power Button (FF) [PWRF]
[17179602.552000] ACPI: Power Button (CM) [PWRB]
[17179602.708000] ibm_acpi: ec object not found
[17179602.744000] pcc_acpi: loading...
[17179603.252000] acpi_cpufreq: Unknown symbol cpu_online_map
[17179606.032000] [drm] Initialized drm 1.0.1 20051102
[17179606.036000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 185
[17179606.040000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179607.552000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179607.552000] apm: overridden by ACPI.
[17179612.236000] eth0: no IPv6 routers present
[17179619.232000] Bluetooth: Core ver 2.8
[17179619.232000] NET: Registered protocol family 31
[17179619.232000] Bluetooth: HCI device and connection manager initialized
[17179619.232000] Bluetooth: HCI socket layer initialized
[17179619.256000] Bluetooth: L2CAP ver 2.8
[17179619.256000] Bluetooth: L2CAP socket layer initialized
[17179619.292000] Bluetooth: RFCOMM socket layer initialized
[17179619.292000] Bluetooth: RFCOMM TTY layer initialized
[17179619.292000] Bluetooth: RFCOMM ver 1.7
[17179734.568000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179734.644000] ISO 9660 Extensions: RRIP_1991A
[17179764.132000] wifi0: cannot get RID fdc6 (len=12) - no PRI f/w

```
*snip*
```

[17257812.524000] wlan0: cannot get RID fd48 (len=2) - no PRI f/w
[17259999.168000] usb 4-2: USB disconnect, address 3
[17260596.704000] usb 4-2: new low speed USB device using uhci_hcd and address 4
[17260596.884000] usb 4-2: configuration #1 chosen from 1 choice
[17260596.908000] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /class/input/input4
[17260596.908000] input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.2-2
[17260786.164000] usb 4-2: USB disconnect, address 4
[17262100.640000] usb 4-2: new low speed USB device using uhci_hcd and address 5
[17262100.820000] usb 4-2: configuration #1 chosen from 1 choice
[17262100.844000] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /class/input/input5
[17262100.844000] input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.2-2

```

---

### Post by FrodoB on 2006-12-03
Here are the relevant parts of the dmesg output. We have competing drivers all trying to get ahold of the same device:
```

[17179594.184000] prism2pci_init: prism2_pci.o: 0.2.5 Loaded
[17179594.184000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 193
[17179594.184000] A Prism2.5 PCI device found, phymem:0xf8000000, irq:193, mem:0xe0214000
[17179596.932000] hfa384x_corereset: corereset: Timed out waiting for cmd register.
[17179596.932000] prism2sta_probe_pci: prism2_pci: hfa384x_corereset() failed.

[17179597.056000] ACPI: PCI interrupt for device 0000:02:0b.0 disabled
[17179597.056000] prism2_pci: probe of 0000:02:0b.0 failed with error -5

[17179597.132000] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17179597.132000] orinoco_pci 0.15rc3 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au> & Jean Tourrilhes <jt@hpl.hp.com>)
[17179597.132000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 193
[17179597.132000] orinoco_pci: Detected device 0000:02:0b.0, mem:0xf8000000-0xf8000fff, irq 193
[17179598.376000] orinoco_pci: Busy timeout
[17179598.376000] orinoco_pci: Initial reset failed
[17179598.376000] ACPI: PCI interrupt for device 0000:02:0b.0 disabled
[17179598.376000] orinoco_pci: probe of 0000:02:0b.0 failed with error -110

[17179598.636000] ieee80211_crypt: registered algorithm 'NULL'
[17179598.664000] hostap_pci: 0.4.4-kernel (Jouni Malinen <jkmaline@cc.hut.fi>)
[17179598.668000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 193
[17179598.668000] hostap_pci: Registered netdevice wifi0
[17179598.668000] wifi0: Original COR value: 0xa9
[17179598.672000] wifi0: COR sreset timeout
[17179598.688000] wifi0: __hfa384x_cmd_no_wait(6) - timeout - reg=0xdda9
[17179598.688000] hostap_pci: first command failed - assuming card does not have primary firmware
[17179599.188000] hostap_pci: assuming no Primary image in flash - card initialization not completed
[17179599.188000] wifi0: test Genesis mode with HCR 0x1f
[17179599.188000] wifi0: Original COR value: 0xa9
[17179599.188000] wifi0: COR sreset timeout
[17179599.220000] Readback test failed, HCR 0x1f write 00 e1 a1 ff read 00 ce a1 ce
[17179599.220000] wifi0: test Genesis mode with HCR 0x0f
[17179599.220000] wifi0: Original COR value: 0xa1
[17179599.224000] wifi0: COR sreset timeout
[17179599.252000] Readback test succeeded, HCR 0x0f
[17179599.284000] wifi0: Intersil Prism2.5 PCI: mem=0xf8000000, irq=193
[17179599.284000] wifi0: registered netdevice wlan0

```


You need to blacklist some modules, so you need to add them to the /etc/modprobe.d/blacklist file:

$ sudo gedit /etc/modprobe.d/blacklist

Add records at the end of the file that contain any two of these three, note that is this case prism2_pci is commented out, so that is one we are hoping to use. 
# blacklist prism2_pci
blacklist orinoco_cs
blacklist hostap_pci

Reboot and see if things don't improve. See if only the prism2_pci is loaded in dmesg.

---

### Post by aqualad on 2006-12-03
```
[17179569.184000] Linux version 2.6.17-10-386 (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Fri Oct 13 18:41:40 UTC 2006 (Ubuntu 2.6.17-10.33-386)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[17179569.184000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001f6f0000 (usable)
[17179569.184000]  BIOS-e820: 000000001f6f0000 - 000000001f6ff000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001f6ff000 - 000000001f700000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001f700000 - 000000001f780000 (usable)
[17179569.184000]  BIOS-e820: 000000001f780000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 503MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f6630
[17179569.184000] On node 0 totalpages: 128896
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 124800 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6670
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1f6f8bf7
[17179569.184000] ACPI: FADT (v001 INTEL  NBGV     0x06040000 PTL  0x00000003) @ 0x1f6fef14
[17179569.184000] ACPI: MADT (v001 PTLTD  	 APIC   0x06040000  LTP 0x00000000) @ 0x1f6fef88
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1f6fefd8
[17179569.184000] ACPI: DSDT (v001  INTEL Brkdle_G 0x06040000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:1 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:df800000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1794.365 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.484000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.484000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.504000] Memory: 501776k/515584k available (1829k kernel code, 13188k reserved, 1038k data, 288k init, 0k highmem)
[17179569.504000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.584000] Calibrating delay using timer specific routine.. 3592.54 BogoMIPS (lpj=7185096)
[17179569.584000] Security Framework v1.0.0 initialized
[17179569.584000] SELinux:  Disabled at boot.
[17179569.584000] Mount-cache hash table entries: 512
[17179569.584000] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.584000] CPU: After vendor identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.584000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179569.584000] CPU: L2 cache: 128K
[17179569.584000] CPU: After all inits, caps: 3febfbff 00000000 00000000 00000080 00000000 00000000 00000000
[17179569.584000] CPU: Intel(R) Celeron(R) CPU 1.80GHz stepping 03
[17179569.584000] Checking 'hlt' instruction... OK.
[17179569.600000] SMP alternatives: switching to UP code
[17179569.600000] Freeing SMP alternatives: 0k freed
[17179569.600000] checking if image is initramfs... it is
[17179570.312000] Freeing initrd memory: 5182k freed
[17179570.312000] ACPI: Core revision 20060707
[17179570.312000] ACPI: Looking for DSDT ... not found!
[17179570.316000] ENABLING IO-APIC IRQs
[17179570.316000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179570.460000] NET: Registered protocol family 16
[17179570.460000] EISA bus registered
[17179570.460000] ACPI: bus type pci registered
[17179570.460000] PCI: PCI BIOS revision 2.10 entry at 0xfd99a, last bus=2
[17179570.460000] PCI: Using configuration type 1
[17179570.460000] Setting up standard PCI resources
[17179570.492000] ACPI: Interpreter enabled
[17179570.492000] ACPI: Using IOAPIC for interrupt routing
[17179570.492000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.492000] PCI: Probing PCI hardware (bus 00)
[17179570.492000] Boot video device is 0000:00:02.0
[17179570.496000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179570.496000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179570.496000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.496000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.496000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.500000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SLOT._PRT]
[17179570.500000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[17179570.500000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[17179570.500000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[17179570.500000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[17179570.504000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179570.504000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179570.504000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[17179570.504000] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 7 9 10 11 12 14 15)
[17179570.508000] ACPI: Power Resource [FN01] (on)
[17179570.508000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.508000] pnp: PnP ACPI init
[17179570.532000] pnp: PnP ACPI: found 10 devices
[17179570.532000] PnPBIOS: Disabled by ACPI PNP
[17179570.536000] PCI: Using ACPI for IRQ routing
[17179570.536000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.540000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179570.540000] PCI: Bridge: 0000:00:1e.0
[17179570.540000]   IO window: 2000-2fff
[17179570.540000]   MEM window: e8100000-e81fffff
[17179570.540000]   PREFETCH window: disabled.
[17179570.540000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.540000] NET: Registered protocol family 2
[17179570.580000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.580000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179570.580000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[17179570.580000] TCP: Hash tables configured (established 16384 bind 8192)
[17179570.580000] TCP reno registered
[17179570.580000] Simple Boot Flag at 0x3b set to 0x1
[17179570.580000] * This chipset may have PM-Timer Bug.  Due to workarounds for a bug,
[17179570.580000] * this time source is slow. If you are sure your timer does not have
[17179570.580000] * this bug, please use "pmtmr_good" to disable the workaround
[17179570.580000] audit: initializing netlink socket (disabled)
[17179570.580000] audit(1165186041.580:1): initialized
[17179570.580000] VFS: Disk quotas dquot_6.5.1
[17179570.580000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.580000] Initializing Cryptographic API
[17179570.580000] io scheduler noop registered
[17179570.580000] io scheduler anticipatory registered
[17179570.580000] io scheduler deadline registered
[17179570.580000] io scheduler cfq registered (default)
[17179570.580000] isapnp: Scanning for PnP cards...
[17179570.936000] isapnp: No Plug & Play device found
[17179571.036000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.036000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.040000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.040000] mice: PS/2 mouse device common for all mice
[17179571.040000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.040000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.040000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.040000] PNP: PS/2 Controller [PNP0303:KBC0] at 0x60,0x64 irq 1
[17179571.040000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179571.052000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.052000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.052000] EISA: Probing bus 0 at eisa.0
[17179571.052000] Cannot allocate resource for EISA slot 1
[17179571.052000] Cannot allocate resource for EISA slot 2
[17179571.052000] EISA: Detected 0 cards.
[17179571.052000] TCP bic registered
[17179571.052000] NET: Registered protocol family 1
[17179571.052000] NET: Registered protocol family 8
[17179571.052000] NET: Registered protocol family 20
[17179571.052000] Using IPI Shortcut mode
[17179571.056000] ACPI: (supports S0 S1 S3 S4 S5)
[17179571.056000] Freeing unused kernel memory: 288k freed
[17179571.080000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.260000] Capability LSM initialized
[17179572.324000] ACPI: Transitioning device [FAN1] to D0
[17179572.324000] ACPI: Transitioning device [FAN1] to D0
[17179572.324000] ACPI: Fan [FAN1] (off)
[17179572.332000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179572.340000] ACPI: Thermal Zone [THRM] (-269 C)
[17179573.208000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[17179573.208000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179573.208000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 177
[17179573.208000] ICH4: chipset revision 1
[17179573.208000] ICH4: not 100% native mode: will probe irqs later
[17179573.208000]     ide0: BM-DMA at 0x1860-0x1867, BIOS settings: hda:DMA, hdb:pio
[17179573.208000]     ide1: BM-DMA at 0x1868-0x186f, BIOS settings: hdc:DMA, hdd:pio
[17179573.208000] Probing IDE interface ide0...
[17179573.500000] hda: Maxtor 6E040L0, ATA DISK drive
[17179574.172000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.180000] Probing IDE interface ide1...
[17179574.916000] hdc: Hewlett-Packard CD-Writer cd16f, ATAPI CD/DVD-ROM drive
[17179575.252000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.272000] hda: max request size: 128KiB
[17179575.288000] hda: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179575.288000] hda: cache flushes supported
[17179575.288000]  hda: hda1 < hda5 > hda2 hda3
[17179575.336000] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179575.336000] Uniform CD-ROM driver Revision: 3.20
[17179575.660000] usbcore: registered new driver usbfs
[17179575.660000] usbcore: registered new driver hub
[17179575.660000] USB Universal Host Controller Interface driver v3.0
[17179575.660000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 185
[17179575.660000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179575.660000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179575.660000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179575.660000] uhci_hcd 0000:00:1d.0: irq 185, io base 0x00001800
[17179575.664000] usb usb1: configuration #1 chosen from 1 choice
[17179575.664000] hub 1-0:1.0: USB hub found
[17179575.664000] hub 1-0:1.0: 2 ports detected
[17179575.768000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 193
[17179575.768000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179575.768000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179575.768000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179575.768000] uhci_hcd 0000:00:1d.1: irq 193, io base 0x00001820
[17179575.768000] usb usb2: configuration #1 chosen from 1 choice
[17179575.768000] hub 2-0:1.0: USB hub found
[17179575.768000] hub 2-0:1.0: 2 ports detected
[17179575.872000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 177
[17179575.872000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179575.872000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179575.872000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179575.872000] uhci_hcd 0000:00:1d.2: irq 177, io base 0x00001840
[17179575.872000] usb usb3: configuration #1 chosen from 1 choice
[17179575.872000] hub 3-0:1.0: USB hub found
[17179575.872000] hub 3-0:1.0: 2 ports detected
[17179576.008000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 201
[17179576.008000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179576.008000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179576.008000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[17179576.008000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179576.008000] ehci_hcd 0000:00:1d.7: irq 201, io mem 0xe8080000
[17179576.012000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.012000] usb usb4: configuration #1 chosen from 1 choice
[17179576.012000] hub 4-0:1.0: USB hub found
[17179576.012000] hub 4-0:1.0: 6 ports detected
[17179576.204000] Attempting manual resume
[17179576.228000] kjournald starting.  Commit interval 5 seconds
[17179576.228000] EXT3-fs: mounted filesystem with ordered data mode.
[17179576.720000] usb 3-2: new low speed USB device using uhci_hcd and address 2
[17179576.900000] usb 3-2: configuration #1 chosen from 1 choice
[17179588.324000] Real Time Clock Driver v1.12ac
[17179588.340000] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[17179588.564000] Floppy drive(s): fd0 is 1.44M
[17179588.580000] FDC 0 is a post-1991 82077
[17179588.924000] usbcore: registered new driver hiddev
[17179588.948000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.952000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179588.972000] hw_random: RNG not detected
[17179589.124000] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /class/input/input1
[17179589.124000] input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.2-2
[17179589.124000] usbcore: registered new driver usbhid
[17179589.124000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179589.128000] Linux agpgart interface v0.101 (c) Dave Jones
[17179589.136000] agpgart: Detected an Intel 845G Chipset.
[17179589.136000] agpgart: Detected 8060K stolen memory.
[17179589.152000] agpgart: AGP aperture is 128M @ 0xf0000000
[17179589.316000] input: PC Speaker as /class/input/input2
[17179589.388000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 209
[17179589.388000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179589.704000] intel8x0_measure_ac97_clock: measured 53796 usecs
[17179589.704000] intel8x0: clocking to 48000
[17179589.848000] parport: PnPBIOS parport detected.
[17179589.848000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179589.908000] 8139too Fast Ethernet driver 0.9.27
[17179589.908000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 17 (level, low) -> IRQ 209
[17179589.908000] eth0: RealTek RTL8139 at 0xe0156000, 00:40:2b:27:58:fd, IRQ 209
[17179589.908000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179589.920000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179589.972000] ts: Compaq touchscreen protocol output
[17179590.348000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179590.384000] lp0: using parport0 (interrupt-driven).
[17179590.436000] Adding 498004k swap on /dev/hda5.  Priority:-1 extents:1 across:498004k
[17179590.572000] EXT3 FS on hda2, internal journal
[17179591.368000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179591.396000] NET: Registered protocol family 17
[17179593.236000] ACPI: Power Button (FF) [PWRF]
[17179593.236000] ACPI: Power Button (CM) [PWRB]
[17179593.388000] ibm_acpi: ec object not found
[17179593.428000] pcc_acpi: loading...
[17179593.924000] acpi_cpufreq: Unknown symbol cpu_online_map
[17179595.700000] NET: Registered protocol family 10
[17179595.700000] lo: Disabled Privacy Extensions
[17179595.700000] IPv6 over IPv4 tunneling driver
[17179596.528000] [drm] Initialized drm 1.0.1 20051102
[17179596.584000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 185
[17179596.588000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179598.132000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179598.132000] apm: overridden by ACPI.
[17179605.776000] eth0: no IPv6 routers present
[17179612.436000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179612.500000] ISO 9660 Extensions: RRIP_1991A
[17179612.744000] Bluetooth: Core ver 2.8
[17179612.744000] NET: Registered protocol family 31
[17179612.744000] Bluetooth: HCI device and connection manager initialized
[17179612.744000] Bluetooth: HCI socket layer initialized
[17179613.716000] Bluetooth: L2CAP ver 2.8
[17179613.716000] Bluetooth: L2CAP socket layer initialized
[17179613.860000] Bluetooth: RFCOMM socket layer initialized
[17179613.860000] Bluetooth: RFCOMM TTY layer initialized
[17179613.860000] Bluetooth: RFCOMM ver 1.7

```

That's with just prism commented.

I tried each possibility.  First with only prism commented, then only the 2nd one, etc. but when I restarted every time the wlan0 and wifi0 weren't recognized at all and I got the SIOCGIFFLAGS error: no such device on all of my network monitors.

---

### Post by FrodoB on 2006-12-03
Well try to modprobe the one that is commented out and see if it appears in iwconfig then:

sudo modprobe prism2_pci

If that does not work change which one is commented in the blacklist and modprobe it and then check iwconfig for something.

---

### Post by aqualad on 2006-12-03
Okay, so I tried all of them, both by just changing them then modprobing and by changing -> restarting -> modprobing.  It didn't recognize wifi0 or wlan0 throughout the entire process when I did iwconfig.  So yeah. Any other suggestions? Thanks for the help btw

---

### Post by FrodoB on 2006-12-03
You are using Edgy Eft, correct? If so just install Dapper Drake 6.06 instead, it should just work.  There is a prism2 pci bug in Edgy, see this bug report:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/53748](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/53748)

Dapper is on long term support through some time in 2009 and I don't think you want to build a new kernel, when installing Dapper should only take 10-15 minutes and it will work.

---

### Post by FrodoB on 2006-12-04
Also to get the firmware you need to use:
 
linux-wlan-ng-firmware 
 
from the universe repository.

---

### Post by aqualad on 2006-12-09
Okay, so I'm a bit frazzled now.

On a fresh install of 6.06 this is what I did:

As soon as it was up and running I did

```
sudo apt-get update
sudo apt-get upgrade
```

Then I updated the linux-image because the GUI kept insisting I did. Afterwards I tried my wireless and got the same exact problem. 

I came back to this forum and saw that you had suggested I download the firmware called "linux-wlan-ng-firmware" so I opened my universe repository did an apt-get update and downloaded and installed it but then realized the package just downloads something that actually downloads the full package. So yeah, I then did:

```
sudo linux-wlan-ng-build-firmware-deb
```

It errored, so I got the dependencies and did it again, this time I got the following:

```

austin@austin:~$ sudo linux-wlan-ng-build-firmware-deb
A    prism2-QHZBhp/src/prism2/af010104.hex
A    prism2-QHZBhp/src/prism2/shared.prism2
A    prism2-QHZBhp/src/prism2/pm010102.hex
A    prism2-QHZBhp/src/prism2/ak010104.hex
A    prism2-QHZBhp/src/prism2/ru010803.hex
A    prism2-QHZBhp/src/prism2/rf010804.hex
A    prism2-QHZBhp/src/prism2/README.firmware
A    prism2-QHZBhp/src/prism2/prism2_ssf.pda
A    prism2-QHZBhp/src/prism2/Makefile
A    prism2-QHZBhp/src/prism2/r1010701.hex
Checked out revision 1807.
dpkg-buildpackage: source package is linux-wlan-ng
dpkg-buildpackage: source version is 0.2.3-1ubuntu7
dpkg-buildpackage: source changed by Martin Pitt <martin.pitt@ubuntu.com>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh_clean debian/postinst
rm -f build-stamp install-stamp
 dpkg-source -b prism2-QHZBhp
dpkg-source: warning: source directory `./prism2-QHZBhp' is not <sourcepackage>-<upstreamversion> `linux-wlan-ng-0.2.3'
dpkg-source: building linux-wlan-ng in linux-wlan-ng_0.2.3-1ubuntu7.tar.gz
dpkg-source: building linux-wlan-ng in linux-wlan-ng_0.2.3-1ubuntu7.dsc
 debian/rules build
touch build-stamp
 fakeroot debian/rules binary
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
# firmware files
mkdir -p debian/tmp/etc/wlan/
cp src/prism2/*pda debian/tmp/etc/wlan/
for x in src/prism2/*.hex ; do \
                if [ -f "$x" ]; then \
                        SUFFIX=`echo $x |  cut -c12-13`;\
                        cp $x debian/tmp/etc/wlan/prism2_$SUFFIX.hex ; \
                fi; \
        done
touch install-stamp
dh_installdirs -i
dh_install -i
dh_installchangelogs -i
dh_installdocs  -i src/prism2/README.firmware
dh_strip  -i
dh_fixperms  -i
dh_shlibdeps  -i
dh_installdeb  -i
dh_gencontrol  -i
dh_compress    -i
dh_md5sums     -i
dh_builddeb    -i
dpkg-deb: building package `linux-wlan-ng-firmware-files' in `../linux-wlan-ng-firmware-files_0.2.3-1ubuntu7_all.deb'.
 dpkg-genchanges
dpkg-genchanges: including full source code in upload
dpkg-buildpackage: full upload; Debian-native package (full source is included)

```

So now what? I don't think it's installed yet but I might actually be getting closer.  This is the last thing I can think of. I would appreciate any help.

---

