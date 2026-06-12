---
title: "Wireless almost working...but need help"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by gnx324 on 2008-03-24
Hi-  I just installed 7.10 on a lenovo T61 and I think it's pretty close to working, but isn't quite there.  any help/insight would be greatly appreciated.  thanks!  Below is the output of various diagnostics/commands.

First of all, I tried setting it up like was suggested in the sticky thread for an unsecured network.  Below is the outcome:
 
```
brian@ubuntu:~$ sudo ifconfig ath0 down
brian@ubuntu:~$ sudo dhclient -r ath0
There is already a pid file /var/run/dhclient.pid with pid 7799
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:1f:3a:66:d5:46
Sending on   LPF/ath0/00:1f:3a:66:d5:46
Sending on   Socket/fallback
brian@ubuntu:~$ sudo ifconfig ath0 up
brian@ubuntu:~$ sudo iwconfig ath0 essid "linksys"
brian@ubuntu:~$ sudo iwconfig ath0 mode Managed
brian@ubuntu:~$ sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:1f:3a:66:d5:46
Sending on   LPF/ath0/00:1f:3a:66:d5:46
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Here's the usual stuff:

From lshw:
```
brian@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1c:25:7a:14:c1
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.3-0 ip=192.168.1.10 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:1f:3a:66:d5:46
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

I find it strange that I don't get an 'ath0' network device, seeing that it shows up for if/iwconfig.  Is that something wrong?  I haven't messed around with much, so I think this configuration is about is 'stock' as it gets.

From iwconfig:
```
brian@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=3/70  Signal level=-91 dBm  Noise level=-94 dBm
          Rx invalid nwid:24320  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

And finally ifconfig:
```
brian@ubuntu:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1F:3A:66:D5:46  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:2 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1002 (1002.0 b)  TX bytes:831 (831.0 b)

ath0:avah Link encap:Ethernet  HWaddr 00:1F:3A:66:D5:46  
          inet addr:169.254.6.120  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:1C:25:7A:14:C1  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe7a:14c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8005 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:10581547 (10.0 MB)  TX bytes:548984 (536.1 KB)
          Base address:0x1840 Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:168 (168.0 b)  TX bytes:168 (168.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-1F-3A-66-D5-46-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32350 errors:0 dropped:0 overruns:0 frame:25638
          TX packets:1809 errors:3 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:3596369 (3.4 MB)  TX bytes:131961 (128.8 KB)
          Interrupt:22
```

I'd really love to get the wireless going and avoid having to surf on windows, so any advice/fixes would be great.  thanks again!

---

### Post by which_chick on 2008-03-24
Hrm.  ifconfig gives you the interfaces on your machine.  You're showing

ath0      Link encap:Ethernet
ath0:avah Link encap:Ethernet

^  the ath0:avahi thing is what you get when the ath0 interface can't find an address on its own.

eth0      Link encap:Ethernet  HWaddr 00:1C:25:7A:14:C1  
This is your wired connection, looks good.

lo        Link encap:Local Loopback  
This is loopback.

wifi0     Link encap:UNSPEC  HWaddr 00-1F-3A-66-D5-46-00-00-00-00-00-00-00-00-00-00  

^ What is this?  Is this the wireless?

---------------

From lshw:

*-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: **wifi0**
       version: 01
       serial: 00:1f:3a:66:d5:46
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

Okay.  Here, lshw says that the "logical name" for your wireless is **wifi0**.  I understand that it's an Atheros card, but lshw thinks the logical name is wifi0 and not ath0.

Your iwconfig, though, says that ath0 is the wireless.

My first thing to try would be to go back through the config thing that you did to start and do those commands with wifi0 instead of using ath0.  Let's see what that does.

---

### Post by gnx324 on 2008-03-24
Yeah, I guess I'm confused why iwconfig does nothing with "wifi0" and all the info pertains to "ath0".  I'm also concerned about the fact that anytime I call dhclient it gives me "unknown hardware address type 801"- whether I'm calling the device ath0 or wifi0.  Anyway, I tried what you suggested (ath0 -> wifi0 in the terminal network setup) and got the following:

```
brian@ubuntu:~$ sudo ifconfig wifi0 down
[sudo] password for brian:
brian@ubuntu:~$ sudo dhclient -r wifi0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Sending on   Socket/fallback
brian@ubuntu:~$ sudo ifconfig wifi0 up
brian@ubuntu:~$ sudo iwconfig wifi0 essid "linksys"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wifi0 ; Invalid argument.
brian@ubuntu:~$ sudo iwconfig wifi0 mode Managed
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wifi0 ; Invalid argument.
brian@ubuntu:~$ sudo dhclient wifi0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/wifi0/
Sending on   LPF/wifi0/
Sending on   Socket/fallback
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wifi0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Thanks again!

---

### Post by which_chick on 2008-03-24
I think that the ath0 card takes the arguments for setting-up-wireless a lot better than wifi0 does.  Wifi0 complains about some of the options -- that doesn't seem like it's right at all.  

Hrm.

ifconfig on my box:
```
eth1      Link encap:Ethernet  HWaddr 00:1E:4C:29:EB:AF  
          inet addr:192.168.254.2  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:4cff:fe29:ebaf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          **RX packets:44106** errors:0 dropped:6442 overruns:0 frame:0
          **TX packets:30818** errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59253766 (56.5 MB)  TX bytes:2010220590 (1.8 GB)
          Interrupt:10 

```

This shows my wireless (it's called eth1, for some reason) which is running -- it's the only internet I have going right now.  Look at the packet counts, there.  Now, this machine has been online and doing assorted internet things for three hours.

Now, look at what you posted from your first ifconfig:
```

wifi0     Link encap:UNSPEC  HWaddr 00-1F-3A-66-D5-46-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          **RX packets:32350** errors:0 dropped:0 overruns:0 frame:25638
          **TX packets:1809** errors:3 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:3596369 (3.4 MB)  TX bytes:131961 (128.8 KB)
          Interrupt:22

```

Your wifi0 thing has a huge number of packets.  See that?  32350?  RIght.  It was doing *something* wireless, for real.  It looks like it's *getting* packets anyway.

Thought:  Put it back the way it was, with the commands run through the ath0 interface.  (Sorry about that, but you can up-arrow in the terminal window and it'll repeat the commands for you so that you don't have to retype them.)

Once you have that done, repost your ifconfig, lshw, iwconfig, and a listing of /etc/network/interfaces  

To get that last, type 

```
cat /etc/network/interfaces
```

and it'll put it on the terminal screen, safe from inadvertent changes.  This is nicer than putting the file in an editor if it's the sort of touchy thing that you don't want to mess with accidentally.

Also, try your ifconfig wifi0 (you can ask it for just that interface) a couple of minutes apart to see if the numbers change.

---

### Post by which_chick on 2008-03-24
I'm also concerned about the number of frame errors that you're showing...

```
wifi0     Link encap:UNSPEC  HWaddr 00-1F-3A-66-D5-46-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32350 errors:0 dropped:0 overruns:0 **frame:25638**
          TX packets:1809 errors:3 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:3596369 (3.4 MB)  TX bytes:131961 (128.8 KB)
          Interrupt:22

```

---

### Post by camotito on 2008-03-26
This doesn't help but I have exactly the same problem. This is the output of lshw:
> 
 description: Wireless interface
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wifi0
       version: 01
       serial: 00:17:f2:41:3e:e7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

And this is the ifconfig output:
> ath0      Link encap:Ethernet  HWaddr 00:17:F2:41:3E:E7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:20 dropped:20 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1189 (1.1 KB)  TX bytes:13872 (13.5 KB)

ath0:avah Link encap:Ethernet  HWaddr 00:17:F2:41:3E:E7  
          inet addr:169.254.8.58  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:16:CB:CF:6E:30  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cbff:fecf:6e30/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13446 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6850 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6400210 (6.1 MB)  TX bytes:959270 (936.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3921 (3.8 KB)  TX bytes:3921 (3.8 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-17-F2-41-3E-E7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48623 errors:0 dropped:0 overruns:0 frame:12499
          TX packets:18630 errors:0 dropped:20 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:5477925 (5.2 MB)  TX bytes:1352305 (1.2 MB)
          Interrupt:16 

As you can see is the same case. The output for trying to connect to my unencrypted wireless network through the terminal is exactly the same as well. I tried with both ath0 and wifi0 and get the exact same messages in the same places.

Entering the command ifconfig wifi0 more than once (as suggested) I can see that the number of packets increase considerably. I think this is strange since I am working with an ethernet cable now...
The same test with ath0 shows that the number of packets doesn't increase.

I was using my wireless network without problems until I suspended my laptop. After that it didn't connect (that is usual). Instead of rebooting that is what I normally do I just try to change the password of the network so I could re-enter it again. But ubuntu wouldn't ask me for a password for my network anymore. I tried to configure manually with the graphical interface but it didn't work neither and nothing have worked since then.

My laptop is a first generation Macbook. I will try to update the driver following this: [https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688]("https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688")
Any other suggestion/idea?
Thanks in advance

---

