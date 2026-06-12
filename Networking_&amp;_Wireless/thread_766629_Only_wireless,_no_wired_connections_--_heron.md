---
title: "Only wireless, no wired connections -- heron"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by rhyinem on 2008-04-25
Greets,

I'm having a rough time getting my wired connection running on 8.04.  I'm running on an Asus P5N32 SLI motherboard with onboard LAN and WLAN.  The WLAN seems to be working fine but eth0 and eth1 just dont seem to be working correctly.  Advice?  Help?  Here are some common outputs...

lspci
> 00:00.0 Host bridge: nVidia Corporation Unknown device 0071 (rev c1)
00:00.1 RAM memory: nVidia Corporation Unknown device 007f (rev a1)
00:00.2 RAM memory: nVidia Corporation Unknown device 0075 (rev a1)
00:00.3 RAM memory: nVidia Corporation Unknown device 006f (rev a1)
00:00.4 RAM memory: nVidia Corporation Unknown device 00b4 (rev a1)
00:01.0 RAM memory: nVidia Corporation Unknown device 0076 (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 0078 (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 0079 (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 007a (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 007b (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 007c (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 007d (rev a1)
00:02.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:05.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
01:00.0 VGA compatible controller: ATI Technologies Inc R580 [Radeon X1900]
01:00.1 Display controller: ATI Technologies Inc Unknown device 7260
02:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
03:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)


ifconfig
>   eth1      Link encap:Ethernet  HWaddr 00:18:f3:b7:14:d6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:218 Base address:0x8000 

eth1:avahi Link encap:Ethernet  HWaddr 00:18:f3:b7:14:d6  
          inet addr:169.254.8.162  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:218 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2434 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2434 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:121700 (118.8 KB)  TX bytes:121700 (118.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:08:5f:ff  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fe08:5fff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:37433 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22804 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50505366 (48.1 MB)  TX bytes:2063708 (1.9 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-08-5F-FF-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


I'm thinking that its to do with all of the unknown devices listed in the lspci.  However, I have no idea how to rectify that either.  I'm just getting started with Linux.

Cheers!
ry

---

### Post by superprash2003 on 2008-04-25
dont seem to see eth0 in ifconfig .. have you tried manually setting ip in network manager for eth1?

---

### Post by rhyinem on 2008-04-25
Not yet but I will later... stupid work biting into my fun time!

---

### Post by hessiess on 2008-04-25
I have the P5N32-E sli mobo and internet also dusent work in hardy :(

> have you tried manually setting ip in network manager for eth1?

how do you do this?

---

### Post by superprash2003 on 2008-04-25
system->administration->network go to your network connection(eth0 or wlan0 depends) .. then select Manually assign ip.. then type ip address manually.. in the gateway field enter the ip of the router

---

### Post by hessiess on 2008-04-25
dus'nt seem to be halping.

if i try to assess the rooter (192.168.1.1), I get a connection refused page in FF 

```
a@a-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:59:e2:94  
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe59:e294/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:1
          TX packets:0 errors:0 dropped:360 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:102306 (99.9 KB)
          Interrupt:213 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:1b:fc:61:38:32  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:214 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:140416 (137.1 KB)  TX bytes:140416 (137.1 KB)
```

sorry if im hijacking this thread, isn't much point having 2 about the same problem :).

---

### Post by rhyinem on 2008-04-25
ok I've tried setting eth1 to have a static IP that agrees with my router... still no go.  Any other ideas?

Cheers!

---

### Post by superprash2003 on 2008-04-25
are you able to ping your router? also try ping google.com

---

### Post by ROWDY!!! on 2008-04-25
I'm having the same problem with my wired network connection.
```

lspci | grep "Ethernet "
00:0a.0 Ethernet Controller: NVidia...

```No ip address is being assigned.
I had a custom configuation with gutsy:

/etc/udev/rules.d/70-persistant-net.rules
```

...
#PCI device 0x10de:0x0450 (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ID=="0000:00:0a.0", ATTR{type}=="1", NAME=="eth0"
...

```and /etc/network/interfaces
```

...
auto eth0
iface eth0 inet dhcp
pre-up ifconfig eth0 hw ether xx:xx:xx:xx:xx:xx

```This was in order to make the wired connection in hardy work.

Hardy seems to be using eth1. Commented out the config in 70-persistent-net.rules and uses:
```

...
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{Address}=="xx:xx:xx:xx:xx:xx", ATTR{type}=="1", KERNEL=="eth*", NAME=="eth1"
...

```I tried removing the ATTR{Address} feild and replaced with my old ID feild but that didn't work.

I also updated /etc/network/interfaces with:
```

 ...
 auto eth1
 iface eth1 inet dhcp
 pre-up ifconfig eth1 hw ether xx:xx:xx:xx:xx:xx
 
```But that doesn't seem to help.

I tried configuring it with the network-manager now /etc/network/interfaces only contains configuration for 'lo'.

Will try setting a static ip address now.
Any further suggestions would be greatly appreciated.

[EDIT]: Static ip does not work.

---

### Post by ROWDY!!! on 2008-04-26
*BUMP*
Some more info:
```

OUTPUT OF: dmesg | grep eth
[   19.582815] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   20.101673] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:1b:24:58:8e:4b
[   20.101678] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[   23.577157] Driver 'sd' needs updating - please use bus_type methods
[   23.577359]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   47.546165] eth0: no link during initialization.
[   49.378431] ADDRCONF(NETDEV_UP): eth0: link is not ready

``````

OUTPUT OF: lshw -C network  
*-network
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:58:8e:4b
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes

``````

OUTPUT OF: ifconfig

eth0
  Link encap:Ethernet
  HWaddr 00:1b:24:58:8e:4b
  UP BROADCAST MULTICAST  MTU:1500  Metric:1
  RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x8000 

``````

OUTPUT OF: cat /var/run/network/ifstate
lo=lo

``````

OUTPUT OF: sudo ifup eth0
Ignoring unknown interface eth0=eth0.

``````

OUTPUT OF: sudo ifdown eth0
ifdown: interface eth0 not configured

``````

OUTPUT OF: sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

``````

OUTPUT OF: sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.6 Copyright 2004-2007 
Internet Systems Consortium. All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1b:24:58:8e:4b
Sending on   LPF/eth0/00:1b:24:58:8e:4b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


``````

OUTPUT OF: cat /etc/resolv.conf
### BEGIN INFO#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5456#
### END INFO
search mannix.monash.edu.au

nameserver 130.194.1.99
nameserver 130.194.7.99

```

Interface eth0 not configured?
Will try putting "eth0=eth0" in /var/run/network/ifstate

---

### Post by wakabayashi on 2008-04-26
Hi, I have the same motherboard and the same problem.
Impossible to have a internet connection with Hardy...
I create a post on the French forum...

link [here]("http://forum.ubuntu-fr.org/viewtopic.php?id=211397")

---

### Post by rhyinem on 2008-04-26
I found that this was a bug with the beta and still exists now.  I did this quick fix and it worked!  

"I've had exactly the same problem, however just found the solution:
In the Gusty Tribe 5 live installer, open a terminal:

$ sudo su
# rmmod forcedeth
# modprobe forcedeth msi=0 msix=0
# /etc/init.d/networking restart

Your network interfaces should come back up and actually work now :-)"

---

### Post by rhyinem on 2008-04-26
BTW

To set this as a startup type script thingy...

Run gedit or kwrite as root and open /etc/rc.local
Atl+F2 -> gksu gedit /etc/rc.local on ubuntu
Run -> kdesu kwrite /etc/rc.local on kubuntu

Paste the lines between the comment lines and exit0.
rmmod forcedeth
modprobe forcedeth msi=0 msix=0
/etc/init.d/networking restart

Cheers!
rhy

---

### Post by hessiess on 2008-04-26
thanks, il try that in a munit

---

### Post by hessiess on 2008-04-26
Yay, it works :lolflag:

---

### Post by nonewmsgs on 2008-04-26
Yay!!1

**thanks rhyinem for the answer and hessiess for asking before i did**

---

### Post by nonewmsgs on 2008-04-26
stick a sudo in front of each of those lines when adjusting your /etc/rc.local though;)
so it is in fact

```

gksu gedit /etc/rc.local

```

(and in the middle of the file in between the lines starting with # but you do not start yours with an #, because rc.local ignores lines starting with an #)
```

sudo rmmod forcedeth
sudo modprobe forcedeth msi=0 msix=0
sudo /etc/init.d/networking restart

```

without the sudo's in place it still requires something like 
sudo bash /etc/rc.local

> **rhyinem said:**
> BTW

To set this as a startup type script thingy...

Run gedit or kwrite as root and open /etc/rc.local
Atl+F2 -> gksu gedit /etc/rc.local on ubuntu
Run -> kdesu kwrite /etc/rc.local on kubuntu

Paste the lines between the comment lines and exit0.
rmmod forcedeth
modprobe forcedeth msi=0 msix=0
/etc/init.d/networking restart

Cheers!
rhy

---

### Post by rhyinem on 2008-04-27
Awesome thanks for the further edumacation!

---

### Post by cadavra on 2008-04-27
> **rhyinem said:**
> I found that this was a bug with the beta and still exists now.  I did this quick fix and it worked!  

"I've had exactly the same problem, however just found the solution:
In the Gusty Tribe 5 live installer, open a terminal:

$ sudo su
# rmmod forcedeth
# modprobe forcedeth msi=0 msix=0
# /etc/init.d/networking restart

Your network interfaces should come back up and actually work now :-)"

Hello all, I'm a huge Ubuntu newbie so bear with me.

I tried the above advice and it didn't work for me - I'm sure I was doing something wrong, lol.  What I did was bring up a Terminal window from within Ubuntu (v 8.04) and then I entered all of the above information . . . but unfortunately nothing happened.

Some tips and tricks would be appreciated.
:confused:

- J.

---

### Post by nonewmsgs on 2008-04-27
after you enter all those enter 

```

ping google.com

```
and see what it says.

---

### Post by masoud77 on 2008-05-21
> **rhyinem said:**
> BTW

To set this as a startup type script thingy...

Run gedit or kwrite as root and open /etc/rc.local
Atl+F2 -> gksu gedit /etc/rc.local on ubuntu
Run -> kdesu kwrite /etc/rc.local on kubuntu

Paste the lines between the comment lines and exit0.
rmmod forcedeth
modprobe forcedeth msi=0 msix=0
/etc/init.d/networking restart

Cheers!
rhy
Thanks a lot, rhyinem for the post. I am able to connect to the internet thanks to your post. 
I have made the changes you have mentioned to the /etc/rc.local file, yet my network isn't up until I run procedure manually after booting up. Is there a way to check whether the scripts in /etc/rc.local is running at all and if so whether it is running as expected (where do I see the logs).
Any help appreciated.

Thanks,
Masoud A R.

---

### Post by larubbio on 2008-06-23
This suggestion did not work for me.  When I ran rmmod I got an error saying module forcedeth does not exist in /proc/modules.  Is it always that module or is there a different one I might need to remove?

For some more detail I am using an HP desktop, I do have a wireless network, but I am using a wired connection.  HP may have put a wireless card in the pc, I'm not sure.  

ifconfig shows eth0:avahi as getting the default ip, eth0 does not get an ip.  I disabled roaming in network manager.  Sometimes on reboot networking works, often it does not.  Other laptops and desktops use dhcp on my router without an issue (Windows and Mac).

---

