---
title: "ipw2100/dhcp problem - I'm really close though"
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by JohnSBA on 2007-11-06
hi gurus, need someone to help push me over the fence here, I'm really close to having wireless working.  Toshiba Tecra M2 laptop, wireless is an Intel Pro/Wireless 2100 with new gutsy install.  wireless recognized, able to scan for access points, but DHCP will not acquire the IP address...  wired connection on the laptop is working fine.  access point is "San Diego", no encryption in the examples below.  I've attempted to connect to two different access points, one with WEP, one without, same failure in DHCP.

Help!!!  System info below, all help appreciated.

```

dmesg shows:
[   16.508000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   16.508000] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   16.508000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKC] -> GSI 11 (lev
el, low) -> IRQ 11
[   16.508000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection

```

```

jcf@jcf-laptop:$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth1
       version: 04
       serial: 00:0c:f1:49:06:ca
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=64 maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 83
       serial: 00:0e:7b:1d:0a:11
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A ip=129.153.94.57 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes

```

```

jcf@jcf-laptop:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      unassociated  ESSID:"San Diego"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```

jcf@jcf-laptop:~$ iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:15:2C:4B:DE:A0
                    ESSID:"San Diego"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:56  Signal level:0  Noise level:0
                    Extra: Last beacon: 192ms ago
          Cell 02 - Address: 00:15:2C:4B:AC:00
                    ESSID:"San Diego"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:37  Signal level:0  Noise level:0
                    Extra: Last beacon: 192ms ago
          Cell 03 - Address: 00:15:2C:48:B6:10
                    ESSID:"San Diego"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:29  Signal level:0  Noise level:0
                    Extra: Last beacon: 144ms ago
          Cell 04 - Address: 00:15:2C:4B:DA:10
                    ESSID:"San Diego"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:33  Signal level:0  Noise level:0
                    Extra: Last beacon: 2068ms ago
          Cell 05 - Address: 00:15:2C:4B:DE:E0
                    ESSID:"San Diego"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:23  Signal level:0  Noise level:0
                    Extra: Last beacon: 10528ms ago

```

```

jcf@jcf-laptop:~$ sudo dhclient eth1
[sudo] password for jcf:
There is already a pid file /var/run/dhclient.pid with pid 7038
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0c:f1:49:06:ca
Sending on   LPF/eth1/00:0c:f1:49:06:ca
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by kevdog on 2007-11-06
Take the space out of the essid name.  See if that works.

---

### Post by JohnSBA on 2007-11-06
> **kevdog said:**
> Take the space out of the essid name.  See if that works.

No change.  My other access point (at home) is a single word no space and same result...

```

jcf@jcf-laptop:~$ sudo iwconfig eth1 essid "SanDiego"
[sudo] password for jcf:
jcf@jcf-laptop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 7516
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0c:f1:49:06:ca
Sending on   LPF/eth1/00:0c:f1:49:06:ca
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by Lambert on 2007-11-06
According to the iwconfig output, you're not associated with the AP so you can't use dhclient until that happens.

Try running this command first.

```

sudo iwconfig eth1 channel 1 essid San Diego

```

run iwconfig to make sure it says you're associated then try the dhclient command.

Of course depending if you put the space back in, adjust SanDiego

---

### Post by JohnSBA on 2007-11-06
The channel subcommand is puking out on iwconfig:

```

jcf@jcf-laptop:~$ sudo iwconfig eth1 channel 1 essid San Diego
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Operation not supported.

```

I've tried many variations of this using channel and freq, but all with same result.  

it seems the issue does relate to my interface being unassigned when I attempt DHCP.  Without looking through the code, what constitutes assignment.  I thought it was simply assigning an essid to the interface, apparently not.

Thank you for your suggestions - I know we will nail this!

---

### Post by Lambert on 2007-11-06
> **JohnSBA said:**
> The channel subcommand is puking out on iwconfig:

```

jcf@jcf-laptop:~$ sudo iwconfig eth1 channel 1 essid San Diego
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Operation not supported.

```

I've tried many variations of this using channel and freq, but all with same result.  

it seems the issue does relate to my interface being unassigned when I attempt DHCP.  Without looking through the code, what constitutes assignment.  I thought it was simply assigning an essid to the interface, apparently not.

Thank you for your suggestions - I know we will nail this!

Quote from first post.

> 
access point is "San Diego", no encryption in the examples below


Looking at the scans they all say 

**Encryption key:on**

The steps that happen are

1. After the mobile station authenticates to an AP/router, it sends an Association Request. 
2. The AP/router processes the Association Request. AP/router vendors may have different implementations for deciding whether or not a client request should be allowed. AP/router grants association and responds with a status code of 0 (successful) and the Association ID (AID).  Failed Association Requests include only a status code and the procedure ends. 
3. AP/router forwards frames to/from the mobile station.

The dhclient is run at step 3 and you're stuck on  step 1 I believe. The router is not letting you associate with it. You said you're trying to connect to an unencrypted AP, all scans showed encryption key: on so I'm not sure where the exact problem is but it has to do with not authenticating your pc as a client and letting you associate.

---

### Post by JohnSBA on 2007-11-06
Another user problem resolved!!!!

Lambert nailed it.  The access point that was said to be open, was in fact WEP encrypted.  After assigning the correct key, the network interface associated and DHCP properly configured the interface, which I am now using to type in this reply!

This also helps me understand the failure mode in the previously known encrypted wireless net - which also would not become associated.  There must be something wrong with the key that was being used.

Thank you!  Great community support.  Chalk this one up to operator error.

John

---

