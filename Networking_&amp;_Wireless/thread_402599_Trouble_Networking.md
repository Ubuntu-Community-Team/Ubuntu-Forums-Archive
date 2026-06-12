---
title: "Trouble Networking"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by ribverb on 2007-04-05
I'm new to Ubuntu. I just installed it on an old Dell Dimension 8100. I've hard wired it to the router, but it won't acquire an IP address. Just 127.0.0.1 with a 255. mask. I have no idea how to get it to recognize the signal. Any help is appreciated.

---

### Post by Floppyjoe on 2007-04-06
Can you open a terminal by clicking on Applications/Accessories/Terminal.
Then enter the command:
```
ifconfig
```
and post the results here?

---

### Post by ribverb on 2007-04-06
Here's the ifconfig info:

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

pete@pete-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:B0:D0:16:96:D9  
          inet6 addr: fe80::2b0:d0ff:fe16:96d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13440 errors:0 dropped:0 overruns:28 frame:0
          TX packets:455 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4457744 (4.2 MiB)  TX bytes:154026 (150.4 KiB)
          Interrupt:11 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2050 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2050 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:156884 (153.2 KiB)  TX bytes:156884 (153.2 KiB)

pete@pete-desktop:~$

---

### Post by spd106 on 2007-04-06
Try running this command
```
sudo dhclient eth0
```

If it times out then could you post the output of these commands
```
lspci
sudo lshw -class network
```

---

### Post by oerd on 2007-04-06
agree with ```
sudo dhclient eth0
``` although i have found that (if your interface is configured as "auto") ```
sudo ifup eth0
``` will also activate it trying to acquire the network address dynamically using dhcp.

---

### Post by ribverb on 2007-04-06
I tried all three and nothing. Results of each command are as follows:

pete@pete-desktop:~**$ sudo dhclient eth0**
There is already a pid file /var/run/dhclient.pid with pid 24297
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:b0:d0:16:96:d9
Sending on   LPF/eth0/00:b0:d0:16:96:d9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
pete@pete-desktop:~$ 
[B]
sudo ifup eth0[/B]
ifup: interface eth0 already configured
   

**sudo lshw -class network**
lspci: invalid option -- c
Usage: lspci [<switches>]

-v              Be verbose
-n              Show numeric ID's
-b              Bus-centric view (PCI addresses and IRQ's instead of those seen by the CPU)
-x              Show hex-dump of the standard portion of config space
-xxx            Show hex-dump of the whole config space (dangerous; root only)
-xxxx           Show hex-dump of the 4096-byte extended config space (root only)
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]   Show only devices in selected slots
-d [<vendor>]:[<device>]        Show only selected devices
-t              Show bus tree
-m              Produce machine-readable output
-i <file>       Use specified ID database instead of /usr/share/misc/pci.ids
-D              Always show domain numbers
-M              Enable `bus mapping' mode (dangerous; root only)
-P <dir>        Use specified directory instead of /proc/bus/pci
-H <mode>       Use direct hardware access (<mode> = 1 or 2)
-F <file>       Read configuration data from given file
-G              Enable PCI access debugging
pete@pete-desktop:~$

---

### Post by spd106 on 2007-04-06
That should have been two separate commands giving something like this```
~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
Serial ATA Controller (rev 01)

```
and
```
$ sudo lshw -class network
Password:
  *-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@00:04.0
       logical name: eth0
       version: a1
       serial: 00:0c:76:xx:xx:xx
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=forcedeth driverversion=0.54 duplex=half ip=169.254.x.x link=no multicast=yes port=MII speed=10MB/s
```
rather than one command which gave you that error message.

---

### Post by ribverb on 2007-04-06
Sorry for the confusion, I cut and pasted 3 separate commands and their results. The individual commands are in bold. It just looks like all one command.

---

### Post by ribverb on 2007-04-06
**Is there anything else I can check or post to get a connection? Also, should I repost any information above in a different format? Help! I need to get this computer connected! **

---

### Post by Erlander on 2007-04-06
Check your router settings.  I s DHCP turned on?

Rob

---

### Post by ribverb on 2007-04-06
DHCP is turned on. Also, I'll repost the results of my commands below:

lshw command results:
```
 *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@02:0c.0
       logical name: eth0
       version: 78
       serial: 00:b0:d0:16:96:d9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=3c59x duplex=full link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:ec00-ec7f iomemory:ff9efc00-ff9efc7f irq:11
pete@pete-desktop:~$ 
```

lspci command results:
```
pete@pete-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 02)
01:00.0 VGA compatible controller: Matrox Graphics, Inc. G400/G450 (rev 82)
02:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:0a.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
02:0b.0 Communication controller: Conexant HCF 56k Data/Fax/Voice/Spkp Modem (rev 08)
02:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
pete@pete-desktop:~$ 

```

---

### Post by Floppyjoe on 2007-04-06
What version of Ubuntu are you running?

---

### Post by ribverb on 2007-04-06
using Edgy

---

### Post by Floppyjoe on 2007-04-06
> **ribverb said:**
> 
pete@pete-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:B0:D0:16:96:D9  
          inet6 addr: fe80::2b0:d0ff:fe16:96d9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13440 errors:0 dropped:0 overruns:28 frame:0
          TX packets:455 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4457744 (4.2 MiB)  TX bytes:154026 (150.4 KiB)
          Interrupt:11 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2050 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2050 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:156884 (153.2 KiB)  TX bytes:156884 (153.2 KiB)


On eth0 here it looks like you are transmitting and recieving packets. It seems strange that it would not show an IP address.

---

### Post by ribverb on 2007-04-06
I'm open to suggestions. :)

---

### Post by Buster95 on 2007-04-06
I had what seems to be the same problem. I could ping but not raise a web page. I was advised to disable ipv6. That worked for me.
Cheers

---

### Post by ribverb on 2007-04-06
I'm new to all this, so I don't know how to disable ipV6. And isn't that to improve connection speed? I do not get a connection at all.

---

### Post by Erlander on 2007-04-07
Have you tried turning off DHCP in the router and then giving your pc's each a static address.

System/Administration/Network.

Rob

---

### Post by ribverb on 2007-04-07
no, was hoping not to have to do that. If it helps, when I connect the cable modem directly to the computer, i get a connection. Now I just need to make it work with the router.

---

