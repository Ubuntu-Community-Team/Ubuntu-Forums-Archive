---
title: "Wake-on LAN on Realtek R8169 (r8169) with Ubuntu 7.04"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by mathewfer on 2007-06-12
Hi Friends

I installed Ubuntu 7.04 on Asus P2-P5945G Barebone with Intel CORE 2 DUO E6600 (Conroe) & 2G  (1x2) Kingston RAM (KVR667D2N5/1G) & all worked fine as expected by me except for the wake-on LAN.

This box has BIOS support for the Wake-on LAN but I have not tested with any other OSs (like XP).

After checking many in this forum, I even used the driver R1000 with no success with WOL.
I am currently running R1000 driver.

See below some of my captures that may help you to help me.

My question are;

1. Has anybody successful in getting the Wake-on LAN feature on this Ubuntu 7.04 with this NIC driver (r8169)?
2. If yes, can you please share your experiences or how you got it to work?
3. If not, can someone let me know whether this driver that comes with Ubuntu 7.04 has the ability for the Wake-on LAN for this NIC driver?

I will appreciate very much if one of you let me know the road-map to get this done.
As I am very happy with this Ubuntu 7.04 for all my requirements, I believe there will be a way to get this Wake-on LAN working with your help.


UbuntuPC@UbuntuPC-desktop:~$ sudo lspci | grep 'Ethernet'
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
UbuntuPC@UbuntuPC-desktop:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 01
       serial: 00:18:f3:ef:73:b6
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r1000 driverversion=1.05 duplex=full firmware=N/A ip=192.168.1.30 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:e800-e8ff iomemory:dffff000-dfffffff irq:16
UbuntuPC@UbuntuPC-desktop:~$

UbuntuPC@UbuntuPC-desktop:~$
UbuntuPC@UbuntuPC-desktop:~$ sudo ethtool eth0
Password:
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Link detected: yes
UbuntuPC@UbuntuPC-desktop:~$ sudo ethtool -s eth0 wol g
Cannot get current wake-on-lan settings: Operation not supported
  not setting wol
UbuntuPC@UbuntuPC-desktop:~$ sudo ethtool -i eth0
driver: r1000
version: 1.05
firmware-version: N/A
bus-info: 0000:02:00.0
UbuntuPC@UbuntuPC-desktop:~$

Thanks for the reply.

Mathew

---

### Post by dogatemycomputer on 2007-06-13
> **mathewfer said:**
> Hi Friends
After checking many in this forum, I even used the driver R1000 with no success with WOL.
I am currently running R1000 driver.


I have a Dell Optiplex 745 running Kubuntu Feisty 7.04 with linux 2.6.20-16-generic.    I'm willing to bet the problem you are having is the kernel is forcing your NIC down at shutdown.  This is normal behavior:

```
walkerd@linux:/etc/acpi/resume.d$ man reboot | grep -i -A2 unnecessary
Reformatting reboot(8), please wait...
              is unnecessary as the kernel will do this anyway.

[B]       -i     Iterates  configured  network  interfaces  and  brings them down
              before shutting down.  On Linux, this is unnecessary as the ker&#8208;
              nel will do this anyway.[/B]

```

The only way I could get it to work was to hibernate or standby the machine.  This creates a file to re-enable WOL when it returns from hibernate or standby:

```
sudo mcedit /etc/acpi/resume.d/63-fixwol.sh
```

containing:

```
#!/bin/sh
ethtool -s eth0 wol g
exit
```

Note that my primary interface is "eth0".  Yours may be eth1 or something else:
```

walkerd@linux:~$ ifconfig
**eth0**      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48145 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:47407080 (45.2 MiB)  TX bytes:13389739 (12.7 MiB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:34429 (33.6 KiB)  TX bytes:34429 (33.6 KiB)

walkerd@linux:~$                                                             

```

This will create a file and add a single line that re-enables WOL if your machine was powered off rather than resuming from standby or hibernate:

> sudo mcedit ~/.bash_login

with this line **(replace eth0 with the appropriate interface!)**:

```
sudo ethtool -s eth0 wol g
```

If your machine won't standby or hibernate (mine won't if you try via K->LOGOFF->HIBERNATE) then I simply execute this script:

```
sudo /etc/acpi/hibernate.sh 
``` 

I associated this script by creating a link in my KDE menu (called, amazingly enough, "Hibernate") and I associated this menu item with CTRL-ALT-H on my keyboard.  This way.. I just press CTRL-ALT-H and it hibernates my machine.  If you need assistance adding an  application to the kicker (K-launch) menu and associating it to a keyboard combination then email me at [email]dogatemycomputer@gmail.com[/email].  I'll be happy to amend this post.

Now.. if you use a router such as a DLink or Linksys and you want to wake your machine over the internet then you need to make sure your machine on your internal network has a static IP address (this way it doesn't move on you) and set your router to forward all **BROADCAST** (very important) traffic from port 9 to port 9 on your PC.  *Of course this only works if you have a dedicated, always-on internet connection, a provider that doesn't filter your port 9 traffic such as cablemodem (or possibly DSL) and a configurable router (for example a DLink, Linksys or Hawkins)*: 

For example.. this is my DLink entry..

```
Edit Virtual Server
Enable : <checked>	
Name : 	 Wake-On-Lan
IP Address : 	 192.168.0.255 **<------  note the private IP address is NOT 192.168.0.1**
Protocol : BOTH	
Protocol Number: 	
Private Port : 	9
Public Port : 9
Inbound Filter : ALLOW ALL 	
	Details : EVERYONE ALLOWED
Schedule : 	ALWAYS
	Details : ALWAYS
```

From there I use [www.dslreports.com/wakeup](www.dslreports.com/wakeup) to boot my machine.  I can boot it from my cell phone..

Someone in another post suggested the following:

```
sudo mcedit /etc/network/interfaces
```

and adding.. 

```
walkerd@linux:/etc/network$ more /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
**up ethtool -s eth0 wol g**

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

walkerd@linux:/etc/network$  
```

This would probably accomplish the same thing as enabling the WOL flag via the .bash_login file but it enables this feature for all users.  There are a couple of other scripts in /etc/init.d/*  that add the "-i" option to the reboot command.  This forces the NIC interfaces down although the man pages indicates these switches are useless because the kernel "will do this anyway".   Unfortunately i'm not brave enough to go in there and start screwing around with the scripts but that might help some people who continue to experience problems with WOL.

One last note for those trying to hibernate your machine.  If it returns from hibernation but you get nothing but a black screen (not white.. black.. dark).. then try CTRL-ALT-F7.   Sometimes it dumps you back to an unused terminal.  I can reproduce that problem on a few machines.

FYI:  The WOL bug is documented here although its probably a duplicate of a few other bug reports:

[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/71418](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/71418)




Good luck!
[email]dogatemycomputer@gmail.com[/email]

---

### Post by mathewfer on 2007-06-13
Hi

Thanks for the detailed reply. I learn a lot from your reply.

The issue I have is it does not respond to the command "ethtool -s eth0 wol g". See below.

By the way, what is your NIC Chipset? What is the output of the command "sudo lspci | grep 'Ethernet'"

Can you please post the output of the below commands?

1. sudo lshw -C network
2. sudo lspci | grep 'Ethernet
3. ethtool eth0 
4. ethtool -s eth0 wol g
5. dmesg | egrep -i r[0-9]{4}
6. lsmod | egrep -i  r[0-9]{4}

UbuntuPC@UbuntuPC-desktop:~$ sudo ethtool -s eth0 wol g
Cannot get current wake-on-lan settings: Operation not supported
  not setting wol
UbuntuPC@UbuntuPC-desktop:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Link detected: yes
UbuntuPC@UbuntuPC-desktop:~$

Thanks for the reply

Mathew

---

