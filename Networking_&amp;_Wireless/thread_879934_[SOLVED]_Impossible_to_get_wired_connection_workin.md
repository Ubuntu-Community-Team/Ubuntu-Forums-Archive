---
title: "[SOLVED] Impossible to get wired connection working"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by tiyakusa on 2008-08-04
Hi all!

I am trying to make my Sis900 ethernet card working under my favourite OS, but unfortunately it does not...

Here is the situation:
1 set top box operating as gateway, wifi hot spot and ethernet hub.
1 eeepc working well in both wifi and wired configurations.
1 desktop computer based on Asrock MB K7S41GX with integrated Sis900 ethernet card. => This is the issue!

So once I made it worked but now I cannot and I don't figure why.

The lspci returns the Sis card correctly, but ifconfig -a command is weird: it returns 2 interfaces, lo and eth0, but eth0 Hw Adr is 00:00:00:00:00 which is absolutely not the correct MAC address.
The only time I made it working, eth0 was not here, but there was a eth1.

Is anybody can give some clues on what I can do to fix this?

Thank you to all.

Bye

---

### Post by pytheas22 on 2008-08-04
It sounds like some problem with the driver, since it's setting a bogus MAC address.  To figure out which driver it's using, please post the output of:
```

lshw -C Network
```

And please also post this:
```

lspci
lspci -n
```

Hopefully Google will lead to a solution once we have that information.

---

### Post by tiyakusa on 2008-08-04
Hi,

Thx for this so fast answer.

Here are the requested info:

lspci -n
```
00:00.0 0600: 1039:0741 (rev 03)
00:01.0 0604: 1039:0003
00:02.0 0601: 1039:0963 (rev 25)
00:02.1 0c05: 1039:0016
00:02.5 0101: 1039:5513
00:02.7 0401: 1039:7012 (rev a0)
00:03.0 0c03: 1039:7001 (rev 0f)
00:03.1 0c03: 1039:7001 (rev 0f)
00:03.2 0c03: 1039:7002
00:04.0 0200: 1039:0900 (rev 91)
00:09.0 0104: 1095:3512 (rev 01)
00:0a.0 0200: 168c:0013 (rev 01)
01:00.0 0300: 1002:5960 (rev 01)
01:00.1 0380: 1002:5940 (rev 01)
```

lspci
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:09.0 RAID bus controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
00:0a.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)

```

lshw -C Network 
```
  *-network:0 DISABLED    
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.0.6 latency=32 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s
  *-network:1
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: wifi0
       version: 01
       serial: 00:0e:2e:90:71:5b
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.0.2 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
```

Any idea how to enable the network:0?

---

### Post by pytheas22 on 2008-08-04
Please post the output of these commands; hopefully they will get you an IP address (you are using dhcp to serve IPs, right?):
```

sudo ifconfig eth0 down hw ether 00:E0:18:B3:A0:F7
sudo ifconfig up
sudo dhclient eth0
```

---

### Post by tiyakusa on 2008-08-05
So here are the requested info:

I started with
```

sudo ifconfig eth0 down hw ether 00:E0:18:B3:A0:F7
```
Then I did
```

sudo ifdown eth0
```
which returns
```

There is already a pid file /var/run/dhclient.eth0.pid with pid 6155
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:e0:18:b3:a0:f7
Sending on   LPF/eth0/00:e0:18:b3:a0:f7
Sending on   Socket/fallback
```
Next,
```
sudo ifup eth0
```
gives
```

There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:e0:18:b3:a0:f7
Sending on   LPF/eth0/00:e0:18:b3:a0:f7
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.0.7 from 192.168.0.254
DHCPREQUEST of 192.168.0.7 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.7 from 192.168.0.254
bound to 192.168.0.7 -- renewal in 365451 seconds.
```
Finally,
```
sudo dhclient eth0
```
gives
```

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:e0:18:b3:a0:f7
Sending on   LPF/eth0/00:e0:18:b3:a0:f7
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.0.7 from 192.168.0.254
DHCPREQUEST of 192.168.0.7 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.7 from 192.168.0.254
bound to 192.168.0.7 -- renewal in 339213 seconds.
```

So now, it seems that an IP has been addressed to my ethernet card (and it works, i can access the ssh server with it!), but I am not sure to correctly understand how it worked: did we give to the eth0 a fictive MAC address?

What next shall I do to make this behavior the default one on startup?

Thank you for all your so useful info.

---

### Post by pytheas22 on 2008-08-05
I'm glad that fixed it.  Basically what we did was use [MAC-address spoofing]("http://www.irongeek.com/i.php?page=security/changemac") to assign your interface a valid MAC address, since it was getting that weird 00:00:00... one for whatever reason.  And once it had a real MAC, it was able to get an IP and work fine.

To make the fix permanent and automatic, you could write a script to run at boot.  To do that, first type:

```
sudo gedit /etc/init.d/MAC-spoof.sh
```

A file will open up.  Add to it this:

```
#!/bin/bash
#this resets the MAC address of the ethernet interface, because the driver doesn't do it correctly

ifconfig eth0 down hw ether 00:E0:18:B3:A0:F7
ifconfig eth0 up
```

Then save and close the file.

Finally, run these commands so that the script gets added to the boot queue:
```

sudo -s
cd /etc/init.d
chmod +x MAC-spoof.sh
update-rc.d MAC-spoof.sh defaults
```

By the way, I got this idea from another thread, I think in a Mandriva forum somewhere, but I can't figure out the URL.  Also, you could probably spoof your MAC to anything you want; I just picked 00:E0:18:B3:A0:F7 because that's what they used in the other thread.

Let me know if the script makes your ethernet work automatically at boot.  There may be some extra lines that need to be added, but I don't think so.

---

### Post by tiyakusa on 2008-08-05
It works perfectly!
Now I can remove the wifi card, it is so cool!!!

Thank you so much for your support.

Long life to pytheas22 and Ubuntu!!!

---

### Post by pytheas22 on 2008-08-05
I'm glad it's fixed; enjoy Ubuntu!

---

### Post by tiyakusa on 2008-10-22
Hi all,

I reopen this thread as I am going further in my network configuration.

I would like to power on the server with Wake-On Lan.

The issue is that I spoof the MAC address of the ethernet controller card.
Thus, I have no idea at all what is the true MAC address of the controller, so WOL cannot work.

Any idea how I can proceed to retrieve this damned MAC addressed?

Regards,

tiYakusa

---

### Post by pytheas22 on 2008-10-22
The MAC address that it gets spoofed to should be 00:E0:18:B3:A0:F7, since that's the value that's in the script (you could change it to anything).  I'm not familiar with wake-on-LAN configuration, but does this provide all the information you need?

---

### Post by tiyakusa on 2008-10-22
> **pytheas22 said:**
> The MAC address that it gets spoofed to should be 00:E0:18:B3:A0:F7, since that's the value that's in the script (you could change it to anything).  I'm not familiar with wake-on-LAN configuration, but does this provide all the information you need?

No this does not work, as this spoof is done only when OS is on.
WOL is a feature that allows the computer to be powered on via LAN.
A magic packet is sent to the broadcast address (255.255.255.255), telling to MAC address owner to wake-up. BUT the card can only recognise its own address (set in factory).

So I need the original MAC address of my card, but I don't know how to do.

Do you understand what I mean? (maybe my explaination is no clear enough)

---

### Post by pytheas22 on 2008-10-22
Oh sorry, I understand now.

It might say in BIOS somewhere what the address is.  Did you look?  It's also possible (but unlikely) that it's printed on the outside of the ethernet device, if you open your computer.

If not, there's a small chance that it might also mention it somewhere in dmesg.  If you run the command 'dmesg' does it say anything about it?

If that doesn't solve it, the only other thing I can think of is to use Windows to figure it out, although I'm sure you don't want to have to install Windows, then reinstall Ubuntu just to find a MAC address.

---

### Post by tiyakusa on 2008-10-23
Yes, I already thought about BIOS and Win solutions. For BIOS, it is not marked anywhere (it is an embedded controller card on the ASROCK motherboard).
For Win, the solution is quite complex!
There is no marking outside.

I will try dmesg, last chance to get this MAC address...

To be continued...

---

### Post by tiyakusa on 2008-11-06
I finally install Windows on a spare hard drive. Then, retrieving the MAC address was easy.
WOL is now working great!

Thank you all :)

---

