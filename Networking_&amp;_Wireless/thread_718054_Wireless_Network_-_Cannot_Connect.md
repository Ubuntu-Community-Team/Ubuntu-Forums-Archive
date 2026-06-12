---
title: "Wireless Network - Cannot Connect"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by Tdclarke on 2008-03-07
Hey :D
I am having trouble connecting to my wireless internet. I have only just installed Ubuntu 7.10desktop, duel-booting with XP, and no connection can be made, although on Windows it is fine. Not really sure what is wrong, maybe the drivers, but they seem to be recognised so not sure :/
Any help would be greatly appreciated

Some details that may help:

**Wireless Card info:**
Make: Asus
Model: WL-138G V2
Chipset: Broadcom BCM4318
Driver: bcm43xx
Supports network install: Probably Not
Supported in installed system: Yes
Works "out of the box": Partially
Comments: Driver installed in Feisty, lacks firmware. bcm43xx-fwcutter in repos will fetch the firmware
Last Updated: 2007-07-03
Type: PCI
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAsus](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAsus)

```

thomas@thomas-desktop:~$ sudo ifconfig eth1 down 
thomas@thomas-desktop:~$ sudo dhclient -r eth1 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

Listening on LPF/eth1/00:17:31:a2:d2:71 
Sending on   LPF/eth1/00:17:31:a2:d2:71 
Sending on   Socket/fallback 
thomas@thomas-desktop:~$ sudo ifconfig eth1 up 
SIOCSIFFLAGS: No such file or directory 
thomas@thomas-desktop:~$ sudo iwconfig eth1 essid "Default" 
thomas@thomas-desktop:~$ sudo iwconfig eth1 key XX:XX:XX:XX:XX 
thomas@thomas-desktop:~$ sudo iwconfig eth1 key open 
thomas@thomas-desktop:~$ sudo iwconfig eth1 mode managed 
thomas@thomas-desktop:~$ sudo dhclient eth1 
There is already a pid file /var/run/dhclient.pid with pid 134519120 
Internet Systems Consortium DHCP Client V3.0.5 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

SIOCSIFFLAGS: No such file or directory 
SIOCSIFFLAGS: No such file or directory 
Listening on LPF/eth1/00:17:31:a2:d2:71 
Sending on   LPF/eth1/00:17:31:a2:d2:71 
Sending on   Socket/fallback 
receive_packet failed on eth1: Network is down 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 
send_packet: Network is down 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4 
send_packet: Network is down 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9 
send_packet: Network is down 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9 
send_packet: Network is down 
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6 
send_packet: Network is down 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 

```

```
thomas@thomas-desktop:~$ sudo lshw -C network 
  *-network DISABLED      
       description: Wireless interface 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 6 
       bus info: pci@0000:05:06.0 
       logical name: eth1 
       version: 02 
       serial: 00:17:31:a2:d2:71 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master ethernet physical wireless 
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=32 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g 
thomas@thomas-desktop:~$ sudo ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:13:D4:9E:57:7D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:18 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 

```

:confused:

Please just ask if any more information is required :)

---

### Post by Presto123 on 2008-03-07
Have you tried following steps like here:
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM43xx_(all,_ndiswrapper/firmware)?highlight=(WifiDocs%2FDevice](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM43xx_(all,_ndiswrapper/firmware)?highlight=(WifiDocs%2FDevice))

---

### Post by uberlube on 2008-03-07
Use the howto in my sig. Hope it helps. :)

---

### Post by Tdclarke on 2008-03-08
**@Presto123**
Right, I will need to buy/borrow some cable, as I have about a metres length spare at the moment, and that's not long enough to get to my router :/ I will hopefully be able to get some over the next few days, otherwise if not, I will just move my PC downstairs right next to my router and use the small amount of cable I do have. 

So basically I will have to update a number of files/drivers on ubuntu?

> utilizing the Ndiswrapper program available at [http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/) . Driver documentation and listing of usable drivers will be located at [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/) .)
So do I have to download a specific versions to be compliant with my driver? 
I'm presuming this:

> 13. Card: Belkin 54g Wireless G Desktop Card (F5D7000) Rev4000

    *
      Chipset: BCM4318
    *
      Driver: Driver: ndiswrapper v1.3 with bcmwl5a.inf [ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/) (Broadcom, 12/22/2004, v3.100.46.0)
    *
      Other: 10/29/2005 - added this entry because Belkin is now using this Broadcom chipset and not the rt2500 anymore. A pity as the rt2500 has awesome native linux drivers. Ndiswrapper works beautifully on my Slack 10.2 desktop with 2.6.13 kernel.

Is mine?
So I will then download the driver - [ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/) - ?
However, [that link](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/) does not seem to work (certainly on XP) and says:
> 550/notebook/aspire_3020_5020/driver/: No such file or directory
Is this a problem?

Sorry for all the questions, I just want to ensure everything is correct before I try it out :)

**@Uberlube**
I tried out your guide (as well as many others on this forum) before creating this new thread. I got to where it is bold (see below), and then it could not locate the executable - Presumably because I have no connection :?

> echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist
echo "blacklist ssb" >> /etc/modprobe.d/blacklist
echo "blacklist b43" >> /etc/modprobe.d/blacklist
echo "alias eth1 ndiswrapper" >> /etc/modprobe.d/ndiswrapper
echo "alias eth1 ndiswrapper" >> /etc/modprobe.conf
echo "ndiswrapper" >> /etc/modules
mkdir /root/wireless_driver
cd /root/wireless_driver/
[B]wget [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)
unzip -a R151517.EXE
cd DRIVER
ndiswrapper -i bcmwl5.inf
modprobe ndiswrapper
reboot[/B]

Thanks a lot for your help guys :)

---

### Post by Presto123 on 2008-03-09
Well...going by his way of Ndiswrapper, it is essentially canceling out my method, but isn't a wrong way to go. It might just take some more time to set up.

---

