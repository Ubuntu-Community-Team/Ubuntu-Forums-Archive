---
title: "AR5212 Wireless card not working in Feisty"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by fallingleaf on 2007-04-22
I did a clean install of Feisty (Kubuntu) yesterday and I was hoping to have better luck with wireless than I did with Edgy.  I went to System Settings->Network Settings and saw my wireless and wired networking listed there.  I configured the wireless for DHCP and put in the ESSID, and then enabled the adapter, but it didn't pick up an IP address.  Then I found KnetworkManager in the taskbar and tried setting it up there.  It showed I had a signal but when I tried to switch to wireless it stuck at 28% in the connection phase.  I tried some other stuff I found in these forums and now the wireless doesn't show up in KnetworkManager any more.  It is still listed in Network Settings.

The adapter is listed in lspci as:
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

/etc/network/interfaces is:

[INDENT]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet dhcp

iface ath0 inet dhcp
wireless-essid myessid
[/INDENT]

This is a Thinkpad T60

---

### Post by fallingleaf on 2007-04-23
Here is some more info:

ifconfig -a
ath0      Link encap:Ethernet  HWaddr 00:16:CF:B3:31:82
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:60 (60.0 b)  TX bytes:0 (0.0 b)

ath0:avah Link encap:Ethernet  HWaddr 00:16:CF:B3:31:82
          inet addr:169.254.7.28  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:15:58:7D:4F:6B
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:fe7d:4f6b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:92202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77277 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:102003473 (97.2 MiB)  TX bytes:10480541 (9.9 MiB)
          Base address:0x3000 Memory:ee000000-ee020000

irda0     Link encap:IrLAP  HWaddr 00:00:00:00
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:89042 (86.9 KiB)  TX bytes:89042 (86.9 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-16-CF-B3-31-82-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:220811 errors:0 dropped:0 overruns:0 frame:71770
          TX packets:90880 errors:4 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:14333748 (13.6 MiB)  TX bytes:4440548 (4.2 MiB)
          Interrupt:21

---

### Post by webdr on 2007-04-23
Check this thread, may help.
[http://ubuntuforums.org/showthread.php?t=420627&highlight=wireless](http://ubuntuforums.org/showthread.php?t=420627&highlight=wireless)

---

### Post by fallingleaf on 2007-04-24
Thanks webdr.  I had tried the new version of madwifi before without success.  I tried installing the new network-manager.  I finally got all the dependencies and got through configure but when I tried  to make it died with this error:

[INDENT]make[2]: Entering directory `/home/noble/NetworkManager-0.6.5/po'
file=`echo ar | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file ar.po
/bin/sh: -o: not found
make[2]: *** [ar.gmo] Error 127
make[2]: Leaving directory `/home/noble/NetworkManager-0.6.5/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/noble/NetworkManager-0.6.5'
make: *** [all] Error 2
[/INDENT]

I'm certainly over my head here.

---

### Post by piNNoy on 2007-05-05
did you ever get it working? i have the same computer. same card.

thinkpad r60

AR5212 802.11abg NIC 

.............pls help if u got it working 

im frustrated =P

---

### Post by Candace on 2007-05-05
Hi,
From reading the forums, it seems like there may be some problems with Atheros, don't really know, but aside, this is what I did to get my wireless card working with Feisty, so it might be worth a try.  I have an HP laptop (wireless card Broadcom Dell 1390 WLAN MiniPCI). These instructions are very simple to follow, even for a newbie like me. :) They are good for a fresh Ubuntu install.

1. [http://ubuntuforums.org/showthread.p...spiron+E1](http://ubuntuforums.org/showthread.p...spiron+E1) 505
2. [http://ubuntuforums.org/showthread.p...22#post2589722](http://ubuntuforums.org/showthread.p...22#post2589722)
3. Encrypting your connection (I don't have this working yet):
[http://ubuntuforums.org/showthread.php?t=202834&page=40](http://ubuntuforums.org/showthread.php?t=202834&page=40)

Hope that helps.

---

### Post by piNNoy on 2007-05-05
> **Candace said:**
> Hi,
From reading the forums, it seems like there may be some problems with Atheros, don't really know, but aside, this is what I did to get my wireless card working with Feisty, so it might be worth a try.  I have an HP laptop (wireless card Broadcom Dell 1390 WLAN MiniPCI). These instructions are very simple to follow, even for a newbie like me. :) They are good for a fresh Ubuntu install.

1. [http://ubuntuforums.org/showthread.p...spiron+E1](http://ubuntuforums.org/showthread.p...spiron+E1) 505
2. [http://ubuntuforums.org/showthread.p...22#post2589722](http://ubuntuforums.org/showthread.p...22#post2589722)
3. Encrypting your connection (I don't have this working yet):
[http://ubuntuforums.org/showthread.php?t=202834&page=40](http://ubuntuforums.org/showthread.php?t=202834&page=40)

Hope that helps.

your top 2 links didnt work

---

### Post by Candace on 2007-05-05
What about now?

1. [http://ubuntuforums.org/showthread.php?p=2589722#post2589722](http://ubuntuforums.org/showthread.php?p=2589722#post2589722)

OR this: [http://ubuntuforums.org/showthread.php?p=2589722](http://ubuntuforums.org/showthread.php?p=2589722) and scroll to the bottom of page 2

2. [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

Let me know if those work.

---

### Post by fallingleaf on 2007-05-05
Both those links refer to using ndiswrapper.  We are using an Atheros chipset that requires the madwifi driver.  However, looking at the top of the page on the first link,  I noticed it suggested removing network-manager and installing [Wicd]("http://wicd.sourceforge.net/").  I installed it, and immediately was without internet.   I searched around and finally located /opt/wicd/tray-edgy.py.  Running this got me a tray icon and the rest was pretty self explanatory.  

Now I have wireless! ... Sort of.  I'm sitting 5 feet from the router right now and if I walk to the other side of the room I no longer have internet .  The connection still shows 40% signal strength, but I cant even ping the router.

At least it's some progress.

---

### Post by fallingleaf on 2007-05-11
Well, I've made more progress.  I had resisted installing ndiswrapper before because my chipset was not listed in the supported chipsets, and because I didn't really know how to go about it.  I downloaded the WinXP driver from Lenova and ran the .exe with Wine to unpack the files.  I installed ndiswrapper, ndiswrapper-utils, and ndisgtk.  I had to remove the madwifi modules:

```
sudo rmmod ath_pci
sudo rmmod ath_hal
```

I also went to *System->Administration->Restricted Drivers Manager *and disabled the Atheros driver there.

Also edited /etc/modules, commenting out ath_pci and putting in ndiswrapper and added "blacklist ath_pci"  to the end of /etc/modprobe.d/blacklist-restricted

Restarted and now it is showing 100% signal strength where before it was giving me %60 right next to the router.  I carried the computer all around the house and never lost connection.  I'm very happy!

---

### Post by dustigroove on 2007-05-20
[FONT=Arial][SIZE=2][COLOR=Black]Thanks fallingleaf, your post was the nudge I needed to stop banging my head trying to get the madwifi drivers working for this card and just go forward with using ndiswrapper.

Hope you don't mind, I co-opted your resolution for [this thread]("http://ubuntuforums.org/showthread.php?p=2688436#post2688436"). ;)

Cheers,

[/COLOR][/SIZE][/FONT]

---

### Post by mail200752 on 2007-06-01
[FONT=Courier New]I am afraid that I am having no luck with my card.  Here's my setup:

$ iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:18:39:C2:CC:69
                    ESSID:"Voltaplein2"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-29 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  

$ sudo lshw -class network
  *-network:0             
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: e
       bus info: pci@01:0e.0
       logical name: wlan0
       version: 01
       serial: 00:15:e9:a8:9d:d3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=D-Link,03/22/2005,4.0.0.1414 latency=128 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11b
       resources: iomemory:febf0000-febfffff irq:19
 
$  sudo iwconfig  wlan0
wlan0     IEEE 802.11b  ESSID:"Voltaplein2"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate=108 Mb/s   
          Encryption key:3130-3938-4E52-4164-616D   Security mode:restricted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Notice that iwlist reports a strong signal, but iwconfig reports none at all!  When I try to bring this interface up, I get:

$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:15:e9:a8:9d:d3
Sending on   LPF/wlan0/00:15:e9:a8:9d:d3
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
$

It never hears back from the router, never gets an IP address
 
my syslog shows this:

Jun  1 22:31:49 localhost avahi-autoipd(wlan0)[3256]: Found user 'avahi-autoipd' (UID 111) and group 'avahi-autoipd' (GID 111).
Jun  1 22:31:49 localhost avahi-autoipd(wlan0)[3256]: Successfully called chroot().
Jun  1 22:31:49 localhost avahi-autoipd(wlan0)[3256]: Successfully dropped root privileges.
Jun  1 22:31:49 localhost avahi-autoipd(wlan0)[3256]: fopen() failed: Permission denied
Jun  1 22:31:49 localhost avahi-autoipd(wlan0)[3256]: Starting with address 169.254.10.115
Jun  1 22:31:54 localhost avahi-autoipd(wlan0)[3256]: Callout BIND, address 169.254.10.115 on interface wlan0
Jun  1 22:31:54 localhost avahi-daemon[4699]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.10.115.
Jun  1 22:31:54 localhost avahi-daemon[4699]: New relevant interface wlan0.IPv4 for mDNS.
Jun  1 22:31:54 localhost avahi-daemon[4699]: Registering new address record for 169.254.10.115 on wlan0.IPv4.
Jun  1 22:31:58 localhost avahi-autoipd(wlan0)[3256]: Successfully claimed IP address 169.254.10.115
Jun  1 22:31:58 localhost avahi-autoipd(wlan0)[3256]: fopen() failed: Permission denied


I'd sure appreciate help getting this baby going.

TIA




[/FONT]

---

