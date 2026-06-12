---
title: "No IP address assigned"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by DavidLamp on 2007-05-01
I have installed Ubuntu on to a AMD64 HP laptop computer.

When I try to setup a ethernet connection thru the manager it shows conneted.

No IP address is getting assigned to eth0.  I have looked in ifconfig and the gui neworking setup.

When I try to Ping, I get a (no network ) error.

Please Advise.

Thank You,

David J. Lamp

---

### Post by DavidLamp on 2007-05-02
More Information,

If I manually assign an IP address to eth0 it pings properly.

If I run ifconfig it shows no packets have been sent or recieved.

I am still unable to use the network.

Please advise me of anything I can test or do.

Thank You,

David J. Lamp

---

### Post by tlongren on 2007-05-02
I've witnessed this too David, it seems Network Manager is reluctant to get an IP address.  I've witnessed this a few times with a wired connection but seems to happen on a regular basis when using wireless.

I'm convinced this is the problem I'm having with wireless.  I can connect to the AP just fine but never get an IP address so I can't hit the internet.

---

### Post by dbott67 on 2007-05-02
There have been a few threads describing similar issues (i.e. card not activated during boot).

One thing to try is this:

1. Set your network config back to DHCP.
2. Boot the computer and login.
3. Once you reach the desktop, run the following commands from a terminal:
```
scpl@dns2:~$ **ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:E0:29:7C:65:3F
          [COLOR=Red]inet addr:192.168.128.59[/COLOR]  Bcast:192.168.128.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:29ff:fe7c:653f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:287713 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96299 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:294263316 (280.6 MiB)  TX bytes:6018201 (5.7 MiB)
          Interrupt:9 Base address:0x4c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1740 (1.6 KiB)  TX bytes:1740 (1.6 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```
```
scpl@dns2:~$ **sudo ifdown eth0 && sudo ifup eth0**
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:e0:29:7c:65:3f
Sending on   LPF/eth0/00:e0:29:7c:65:3f
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.128.25 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:e0:29:7c:65:3f
Sending on   LPF/eth0/00:e0:29:7c:65:3f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.128.25
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.128.25
bound to 192.168.128.59 -- renewal in 299806 seconds.

```
The first command will just show the current interface status.  The 2nd command will de-activate & re-activate the ethernet card (replace eth0 with the appropriate interface for your computer).

If the NIC grabs an IP from the DHCP server, then you may want to read through this thread:
[http://ubuntuforums.org/showthread.php?t=408647](http://ubuntuforums.org/showthread.php?t=408647)

Page 3 has a work-around script (post #21) and post #30 has something that worked for someone else.

-Dave

---

### Post by DavidLamp on 2007-05-02
I have completed the proccess.

Still does not look correct and is not working.

Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0f:b0:b8:4e:61
Sending on   LPF/eth0/00:0f:b0:b8:4e:61
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0f:b0:b8:4e:61
Sending on   LPF/eth0/00:0f:b0:b8:4e:61
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
applelee@applelee:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:B8:4E:61
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:50 Base address:0x8400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:37 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2912 (2.8 KiB)  TX bytes:2912 (2.8 KiB)

Thank you for any additonal help.

David

---

### Post by ajchen16888 on 2007-05-02
I've encountered a number of problems since installing Feisty and no ip address assigned is one of them.  The following command as suggested by someone on the forum worked for me:

sudo dhclient eth0

Maybe you can give it a go.  Good luck!

---

### Post by dbott67 on 2007-05-03
Hi Dave,

What kind of DHCP server do you have (a D-Link or Linksys router or similar)?  If so, they are just little *nix appliances that can provide a number of services (NAT firewall, routing, DHCP, DNS forwards, etc) and occasionally can lockup.

With DHCP, the IPs are "leased", so it's conceivable that other machines may not indicate any trouble, as they have been previously assigned an IP address and it just re-uses the same number.

Try re-booting the router (cycling the power if there's no on/off switch).  Also check the vendor website for upgrades to the firmware.  I have had devices (that previously worked without problems for a couple of years) all of a sudden stop working.  Nothing had changed on the network, but a firmware upgrade fixed it.

If you're having troubles still, please post the make & model of your router.

-Dave

---

### Post by DavidLamp on 2007-05-03
Dave,

I appreciate your help.

I have completed your request.

I do not think it is the router.

If  I assign a static ID to eth0 and ping it it does not show packets sent or recieved.

lo loopback shows the traffic with no errors.

It is as if the loopback is not sending to the network card.  Or the hardware is not activated.

I did run from the install disk same results.  Reinstalled system several times with same results.

I tried all reccomendations each time same results.

Any other advice?

Thank you.

David

---

### Post by dbott67 on 2007-05-03
Hi David,

Sorry, I may have misunderstood one of your previous posts --- I thought you were able to get online with a static IP, but for some reason your computer was not getting a dynamic IP.  

Can you post the output of the following commands for me please:

*Note: f you have a USB thumb drive (or floppy or some other removable media you can write to) you can use the 'redirect' function to write the output of the commands to a file and then copy them to the USB. Start in your home directory (**cd ~**):*

```
cat /etc/network/interfaces > interfaces.txt
``````
ifconfig -a > ifconfig.txt
``````
sudo lshw -C network > lshw.txt
``````
route -n > route.txt
``````
sudo iptables -L > iptables.txt
```Copy all 5 files to floppy/USB, bring them over to Windows and then post them here. All five files should be in your home directory.

-Dave

---

### Post by dbott67 on 2007-05-03
By the way, the commands should provide output similar to the information posted below:

1. Network Interfaces file:
```
dbott@feisty:~$ **cat /etc/network/interfaces** 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```2. Interface configuration
```
dbott@feisty:~$ **ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:50:BA:C0:A7:55  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fec0:a755/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:579776 errors:0 dropped:0 overruns:0 frame:0
          TX packets:474754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:385862054 (367.9 MiB)  TX bytes:71295585 (67.9 MiB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:484422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:484422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52744400 (50.3 MiB)  TX bytes:52744400 (50.3 MiB)

```3. Network Hardware
```
dbott@feisty:~$ **sudo lshw -C network**
Password:
  *-network               
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 10
       serial: 00:50:ba:c0:a7:55
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.106 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:b000-b0ff iomemory:be800000-be8000ff irq:16

```4. Routing table:
```
dbott@feisty:~$ **route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```5. Firewall status:
```

dbott@feisty:~$ **sudo iptables -L**
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   
```-Dave

---

### Post by DavidLamp on 2007-05-03
Dave,


I did as requested a few times. I even restarted machine.

Output was the same each time


applelee@applelee:~$
applelee@applelee:~$
applelee@applelee:~$ cat /etc/network/interfaces > interfaces.txt
applelee@applelee:~$ ifconfig -a > ifconfig.txt
applelee@applelee:~$ sudo lshw -C network > lshw.txt
applelee@applelee:~$ route -n > route.txt
applelee@applelee:~$ sudo iptables -L > iptables.txt
applelee@applelee:~$


I could see some information go by very fast.  The output did not show in the Terminal window.

Thank you again.

David

---

### Post by DavidLamp on 2007-05-03
Sorry Dave,

I did cut and paste from your thread without looking at output notes.


Here is the information you needed.

applelee@applelee:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

applelee@applelee:~$  ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:B8:4E:61
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:50 Base address:0xc400

eth1      Link encap:Ethernet  HWaddr 00:14:A5:1D:67:03
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5312 (5.1 KiB)  TX bytes:5312 (5.1 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

applelee@applelee:~$  sudo lshw -C network
Password:
  *-network:0 DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@03:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:1d:67:03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-23-386 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:b0204000-b0205fff irq:177
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:b8:4e:61
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:a000-a0ff iomemory:b020a400-b020a4ff irq:50
applelee@applelee:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
applelee@applelee:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
applelee@applelee:~$


Again, sorry for not being very sharp.

I do appreciate your help.

David

---

### Post by dbott67 on 2007-05-03
Hi David,

There's a number of threads with people having issues with Realtek cards.

One of the solutions is to disable some boot parameters:
[https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems)

Details on how to modify the parameters in grub are here:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

[This guy]("http://ubuntuforums.org/showthread.php?t=402236&highlight=realtek+8139+problems") had success by setting "acpi=off" in the boot parameters.  I posted in another thread on [how to edit the grub menu]("http://ubuntuforums.org/showthread.php?p=2508862#post2508862").  Ultimately, it turned out that the problem was rectified by [resetting the BIOS to default settings]("http://ubuntuforums.org/showthread.php?p=2566254#post2566254"):
> **obz said:**
> Not sure why this worked... but after having tried several ubuntu distros that *i knew worked* on my computer from previous installs ... I figured somehow it *had* to be a hardware problem. I ruled out the NICs, cablesm router. It seems like I was right...

I reset my mobo bios back to original state and tried it. And Voila! I got interweb. What setting was messing up my installs I don't know. I find it really odd. Hopefully this will help someone in some way.

I'm Feisty again. Phew. :)

-Dave

---

### Post by jodoj80 on 2007-05-04
Hi everyone, I'm a newbie in this so I made files from my network information. I hope this help
[LIST=1]
[*]cat /etc/network/interfaces ([COLOR="Red"]I don't understand why the NIC has a TCP/IP configuration if it DHCP enable and I restart the computer[/COLOR]):confused: 
```
auto eth0
iface eth0 inet dhcp
address 10.0.0.50
netmask 255.255.255.0
gateway 10.0.0.1
```
[*]ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:0D:87:3E:D9:10  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:0xdc00 

lo        Link encap:Local Loopback  
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```
[*]sudo lshw -C network```
  *-network
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 74
       serial: 00:0d:87:3e:d9:10
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:dc00-dcff iomemory:dffffe00-dffffeff irq:177
```
[*]route ```
-nKernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```
[*] sudo iptables -L ```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```[/LIST]I do appreciate your help.

---

### Post by dbott67 on 2007-05-04
@DavidLamp:

David, 

I just noticed that your wired interface is eth1 and that it's not enabled in your /etc/network/interfaces file (it's missing the [COLOR=Blue]auto eth1[/COLOR]).

Try this:
```
sudo ifup eth1
```
followed by:
```
sudo dhclient eth1
```

If the interface starts working, edit your interfaces file:
```
sudo gedit /etc/network/interfaces
```
and add the following line:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

[COLOR=Blue]auto eth1[/COLOR]
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

-Dave

---

### Post by dbott67 on 2007-05-04
@jodoj80:

What version of Ubuntu are you running: 6.06 (dapper), 6.10 (edgy) or 7.04 (feisty)?

Can you post the output of [COLOR=Blue]**uname -r**[/COLOR]?

Thanks,
Dave

---

### Post by jodoj80 on 2007-05-04
@Dave

I'm using Edgy 2.6.17-10 generic

---

### Post by DavidLamp on 2007-05-07
Hello Dave,

I am sorry for the delay in responding.

I was called out of town on a family emergency.

I uninstalled Ubuntu from  the computer I was setting up and sent them on their way to China.

I appreciate your help.  They will return in about eight weeks.  I may get a chnace to try again.

Best Regards,

David

---

### Post by dbott67 on 2007-05-08
> **jodoj80 said:**
> @Dave

I'm using Edgy 2.6.17-10 generic
@jodoj80:

Sorry for the delay.  I found this little tidbit for someone with the same card having network troubles:

_**Changing Kernel Parameters:**_

Immediately after booting, grub will give you about 3 seconds to enter the grub menu:

1. Hit '**e**', it will show you the configuration for this booting option.

2. Move to the kernel line with the arrows. It should look like this : 
```
kernel          /vmlinuz-2.6.15-28-k7 root=/dev/mapper/vghda6-lvslash ro vga=791 quiet splash
```

3. Hit '**e**' once again and add the option to this line:

```
kernel          /vmlinuz-2.6.15-28-k7 root=/dev/mapper/vghda6-lvslash ro vga=791 quiet splash [COLOR=Red]noapic[/COLOR]
```

4.  Hit '**enter**', it should show you back the whole config with your modification for this boot only

5. Hit '[COLOR=Black]**b**[/COLOR]' to boot using this configuraiton

If it works then you can set it permanently to your **/boot/grub/menu.lst**.

These are some of the other options you can try:

[B]- noapic 
- nolapic 
- acpi=off 
- pci=noacpi

[/B]-Dave

---

### Post by jodoj80 on 2007-05-13
Hello everyone,

I just want to say that I resolve my issue with the ethernet port. I don't know how but it happens after a few hardware upgrades and some cable changes (not the patch cord, because I used around 5 trying to resolve the old issue). 

@dbott67

Sorry for the delay. A lot of work helping a client to get ISO 9000:2001.

I follow everything that you told me before, but I didn't work at all. I don't know if what you told me to do resolve some part of this issue. I just know that thanks to you I know a little bit more about ethernet issues in Ubuntu.

Thanks dbott67 and everyone that help me with this issue. :guitar:

---

