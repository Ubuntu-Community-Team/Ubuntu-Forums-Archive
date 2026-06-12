---
title: "Broadcom b43xx Wireless on Ibex Not Working"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by sjrlaw on 2008-11-04
Can't get wireless to work.  System > Administrative > Hardware Drivers says that the Broadcom B43 Wireless Driver is activated and currently in use.  However, when I type "lshw -C network" I get the following:

```

  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:01:01.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 01
       serial: 00:0c:f1:c0:a4:d2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.105 latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0c:41:65:e2:97
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.106 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6a:2a:22:d5:0e:58
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

Why is one working and the other disabled?  When I type  "iwconfig wlan0" I get:

```

wlan0     IEEE 802.11bg  ESSID:"exit27"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:E5:A2:AA:C9   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=86/100  Signal level:-46 dBm  Noise level=-67 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

However, when I click on the network icon in the upper right corner, it tells me that the Wireless Networks device is unmanaged.  Help!

---

### Post by Ayuthia on 2008-11-05
> **sjrlaw said:**
> Can't get wireless to work.  System > Administrative > Hardware Drivers says that the Broadcom B43 Wireless Driver is activated and currently in use.  However, when I type "lshw -C network" I get the following:

```

  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:01:01.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 01
       serial: 00:0c:f1:c0:a4:d2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.105 latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0c:41:65:e2:97
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.106 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6a:2a:22:d5:0e:58
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

Why is one working and the other disabled?  When I type  "iwconfig wlan0" I get:

```

wlan0     IEEE 802.11bg  ESSID:"exit27"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:E5:A2:AA:C9   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=86/100  Signal level:-46 dBm  Noise level=-67 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

However, when I click on the network icon in the upper right corner, it tells me that the Wireless Networks device is unmanaged.  Help!
When you do the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe b43
sudo /etc/init.d/networking restart
sudo iwlist scan
```Do you see wireless sites?

---

### Post by sjrlaw on 2008-11-05
This is what I got:

```

 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 4069
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0c:41:65:e2:97
Sending on   LPF/wlan0/00:0c:41:65:e2:97
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
Ignoring unknown interface eth0=eth0.
Ignoring unknown interface eth0=eth0.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0c:41:65:e2:97
Sending on   LPF/wlan0/00:0c:41:65:e2:97
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPOFFER of 192.168.1.106 from 192.168.1.1
DHCPREQUEST of 192.168.1.106 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.106 from 192.168.1.1
bound to 192.168.1.106 -- renewal in 37597 seconds.
 * if-up.d/mountnfs[wlan0]: waiting for interface eth0 before doing NFS mounts
                                                                         [ OK ]
steve@Ubuntu-Workstation:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:E5:A2:AA:C9
                    ESSID:"exit27"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=76/100  Signal level:-55 dBm  Noise level=-70 dBm
                    Encryption key:off
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:tsf=000001223b7093cc
                    Extra: Last beacon: 796ms ago
          Cell 02 - Address: 00:0C:41:79:19:6C
                    ESSID:"exit27a"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/100  Signal level:-72 dBm  Noise level=-70 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=0000016575619185
                    Extra: Last beacon: 348ms ago



```

I have no idea what the first output means, but it looks like wlan0 is scanning okay, although it identifies two ESSIDs for the two access points in my home.  Does this show the problem?

---

### Post by Ayuthia on 2008-11-05
> **sjrlaw said:**
> This is what I got:

```

 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 4069
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0c:41:65:e2:97
Sending on   LPF/wlan0/00:0c:41:65:e2:97
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
Ignoring unknown interface eth0=eth0.
Ignoring unknown interface eth0=eth0.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0c:41:65:e2:97
Sending on   LPF/wlan0/00:0c:41:65:e2:97
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPOFFER of 192.168.1.106 from 192.168.1.1
DHCPREQUEST of 192.168.1.106 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.106 from 192.168.1.1
bound to 192.168.1.106 -- renewal in 37597 seconds.
 * if-up.d/mountnfs[wlan0]: waiting for interface eth0 before doing NFS mounts
                                                                         [ OK ]
steve@Ubuntu-Workstation:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:E5:A2:AA:C9
                    ESSID:"exit27"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=76/100  Signal level:-55 dBm  Noise level=-70 dBm
                    Encryption key:off
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:tsf=000001223b7093cc
                    Extra: Last beacon: 796ms ago
          Cell 02 - Address: 00:0C:41:79:19:6C
                    ESSID:"exit27a"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/100  Signal level:-72 dBm  Noise level=-70 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=0000016575619185
                    Extra: Last beacon: 348ms ago



```

I have no idea what the first output means, but it looks like wlan0 is scanning okay, although it identifies two ESSIDs for the two access points in my home.  Does this show the problem?

The first part is running dhclient to eth0 then wlan0.  Do you have anything in /etc/network/interfaces?

It looks like your wireless is there and working,   Can you try the following to see if it is really connecting:
```
sudo iwconfig wlan0 essid exit27
sudo dhclient wlan0
ping -c1 www.google.com
```
If you restarted you computer, you will have to do the commands in the second post.

---

### Post by Dimoutlook on 2008-11-05
Try this it worked for my 4318 acer laptop

[http://ubuntuforums.org/showthread.php?t=766560&highlight=bcm+4318](http://ubuntuforums.org/showthread.php?t=766560&highlight=bcm+4318)

---

### Post by sjrlaw on 2008-11-05
Ayuthea:

The content of /etc/network/interfaces is as follows:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp


iface wlan0 inet dhcp
wireless-essid any

auto wlan0

```

I unplugged the ethernet cable, so as to use only the wireless card, and ran the three commands you suggested.  I got this:

```

steve@Ubuntu-Workstation:~$ sudo iwconfig wlan0 essid exit27
[sudo] password for steve: 
steve@Ubuntu-Workstation:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0c:41:65:e2:97
Sending on   LPF/wlan0/00:0c:41:65:e2:97
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.1.106 from 192.168.1.1
DHCPREQUEST of 192.168.1.106 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.106 from 192.168.1.1
bound to 192.168.1.106 -- renewal in 41098 seconds.
steve@Ubuntu-Workstation:~$ ping -cl www.google.com
ping: bad number of packets to transmit.
steve@Ubuntu-Workstation:~$ 

```

The network icon next to the volume icon  and date in the upper right corner of the GNOME screen says that the wireless network device is unmanaged.  However, I was able to load web pages in the browser and downloaded system updates as well, so I obviously have a wireless network connection.  Why isn't GNOME telling me I have a wireless network connection?  There are none listed in Wireless Network Connections in the Network Connections app.  What's going on?

---

### Post by Ayuthia on 2008-11-05
> **sjrlaw said:**
> Ayuthea:

The content of /etc/network/interfaces is as follows:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp


iface wlan0 inet dhcp
wireless-essid any

auto wlan0

```

I unplugged the ethernet cable, so as to use only the wireless card, and ran the three commands you suggested.  I got this:

```

steve@Ubuntu-Workstation:~$ sudo iwconfig wlan0 essid exit27
[sudo] password for steve: 
steve@Ubuntu-Workstation:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0c:41:65:e2:97
Sending on   LPF/wlan0/00:0c:41:65:e2:97
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.1.106 from 192.168.1.1
DHCPREQUEST of 192.168.1.106 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.106 from 192.168.1.1
bound to 192.168.1.106 -- renewal in 41098 seconds.
steve@Ubuntu-Workstation:~$ ping -cl www.google.com
ping: bad number of packets to transmit.
steve@Ubuntu-Workstation:~$ 

```

The network icon next to the volume icon  and date in the upper right corner of the GNOME screen says that the wireless network device is unmanaged.  However, I was able to load web pages in the browser and downloaded system updates as well, so I obviously have a wireless network connection.  Why isn't GNOME telling me I have a wireless network connection?  There are none listed in Wireless Network Connections in the Network Connections app.  What's going on?

I am not for sure what the exact cause for this.  It could be because of your /etc/network/interfaces file.  You might comment out everything but the lo section:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp


#iface wlan0 inet dhcp
#wireless-essid any

#auto wlan0
```
And see if it makes a difference.  My thought is that network manager thinks that you want to control it through /etc/network/interfaces, but I could be wrong.  I have not played with that file too much.

---

### Post by sjrlaw on 2008-11-06
You might be right.  My laptop, running Hardy, has Network Manager properly identifying both wired and wireless networks.  The content of its /etc/network/interfaces is:

```


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp

auto eth0


```

Should I switch the Ibex desktop to this?

---

### Post by sjrlaw on 2008-11-07
Ayuthia:

Thank you!  Thank you!  Thank you!!  Your advice was right on the money.  I commented out those lines in /etc/network/interfaces, rebooted, and the Network Manager came up with an icon showing a wireless connection.  Clicking on it also showed all available wireless connections as well as the disconnected wired one!  I am up and running great now, and have learned new things about Linux in the process!  You da bomb!

Steve

---

### Post by v4nilla on 2008-11-08
I too have a broadcom bcm43xx and wireless networking is not working. The card is detected by the hardware troubleshooter, but it does not detect any networks, nor is it listed in /etc/network/interfaces. This is a new install of 8.10 and the file has only 2 lines:

auto lo
iface lo inet loopback

ifconfig shows only eth0 and loopback.
any help would be much appreciated. I am a bit of a n00b. Thanks.

---

### Post by knytphal on 2009-06-26
I know this is an old thread but I also just wanted to thank Ayuthia for thier help.  I've been trying to get the Broadcom wireless working on my Compaq 5000 laptop and this thread was a great help to me.

So, thank you!

---

