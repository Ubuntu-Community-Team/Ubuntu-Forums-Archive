---
title: "[SOLVED] Please help:  can't connect eth0 to network in ubuntu"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by Michl on 2007-10-14
I dual boot on my Dell laptop and am travelling using a LAN connection available
in my office.  In Windows I can connect without a problem and am now in WIndows,
but ubuntu is giving me trouble.  I was able to connect once, but after I rebooted
I was not able to connect even though as far as I could tell I had the very same
settings as before.  I have tinkered with various settings using ethtool (autoneg
off and on, switching the duplex) and nothing helped.

I hope someone can help me get out of Windows because I can just see the smirks
on my colleagues faces if they knew I h ad to crawl back to windows for help --
"told you linux was only for tinkerers and hobbyists with time to waste."

Here is some info that might help:

ethtool eth0 (the setting I have and had when it worked -- autoneg was off):

```
Supported link modes:  10baseT/Half 10baseT/Full
                           100baseT/Half  100baseT/Full
Supports auto-negotiation:  Yes
Advertised link modes:  10baseT/Half 10baseT/Full
                           100baseT/Half  100baseT/Full
Advertised auto-negotiation: No
Speed: 10Mb/s
Duplex Half
Port: MII
PHYAD: 24
Transceiver: internal
Auto-negotiation: off
CUrrent message level:  0x00000001 (1)
Link detected: no
```

I should mentione that sometimes it has link detected yes, but I'm
still not getting connected.

The /etc/network/interfaces file is:
```
auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhsp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface ppp0 inet ppp
provider ppp0

auto ppp0

auto eth0
iface eth0 inet static
address 192.168.156.105
netmask 255.255.255.0
gateway 192.168.156.1
media 10baseT/Half
metric 1
```

Note:  In Windows the key was to change the media type to 10BaseTx and
changing the speed to 10Mb/s was what also made things work in ubuntu
when it worked once.

And finally (I am entering this by hand!) the ifconfig output for the eth0 part:
```
Link encap:Ethernet HWaddr 00:06:5B:E2:18:36
inet addr:192.168.156.105 Bcast:192.168.156.255 Mask:255.255.255.0
inet6 addr:fe80::206:5bff:fee2:1836/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:8262 errors:0 dropped:0 overruns:0 frame:0
TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:583783 (570.1 KiB) TX bytes:468 (468.0 b)
Interrupt:11 Base address:0xcc00
``` 

One more bit of information about something puzzling:
In Network Tools->Devices
It shows that I am receiving bytes and packets!
Also, I can Ping my IP address but not the gateway or any internet
site.

In Connection Properties it shows that I am disconnected
and not packets or bytes have been received.

I hope someone can help, please!!
Michl

---

### Post by noob12 on 2007-10-14
You might want to use a USB jump drive to get text off the box to post.

Can you post or at least indicate what type of device you have and what driver is being used
```

lspci -nn

sudo lshw -C network

```
The line for the ethernet controller and the "configuration" line from the lshw are most interesting if you are retyping excerpts.


Also why do you have ppp0 configured at all?  My totally blind guess is that it is interfering.  What does your route table look like?  
```

route -n

```

What happens if you comment out all of the ppp0 config lines from /etc/network/interfaces?

---

### Post by Michl on 2007-10-14
Thanks for replying!!!   And appreciate the hint to use USB.

Thee output for lspci -nn is:

```
00:00.0 0600: 8086:3575 (rev 04)
00:01.0 0604: 8086:3576 (rev 04)
00:1d.0 0c03: 8086:2482 (rev 02)
00:1e.0 0604: 8086:2448 (rev 42)
00:1f.0 0601: 8086:248c (rev 02)
00:1f.1 0101: 8086:248a (rev 02)
00:1f.5 0401: 8086:2485 (rev 02)
00:1f.6 0703: 8086:2486 (rev 02)
01:00.0 0300: 1002:4c59
02:00.0 0200: 10b7:9200 (rev 78)
02:01.0 0607: 104c:ac51
02:01.1 0607: 104c:ac51
02:03.0 0607: 104c:ac50 (rev 01)
```

route -n out put is
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.156.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.156.1   0.0.0.0         UG    0      0        0 eth0
```

and sudo lshw -C network output is:

```
*-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:e2:18:36
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=off broadcast=yes driver=3c59x duplex=half ip=192.168.156.105 link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:ec80-ecff iomemory:f8fffc00-f8fffc7f irq:11
  *-network
       description: TrueMobile 1150 Series PC Card
       product: Version 01.01
       vendor: Dell
       physical id: 0
       slot: Socket 2
       resources: irq:5
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:5d:6f:7b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15rc3 firmware=Lucent/Agere 6.16 link=no multicast=yes wireless=IEEE 802.11b
```

I have wifi but no signal in this apartment.  The reason for ppp0 is that back in the
US at home I need to use an external modem.  Both the wifi and the modem are not
enabled and both are unchecked.

I limited the speed to 10mB/s because in W2K changing the Media Type to 10BaseTx solved
my problems there.

Thanks again,
Michael

---

### Post by noob12 on 2007-10-14
The sudo lshw output is showing "link=no".  Assuming you've already checked cables and that it is plugged into an active port on the other side of the cable, this might be related to the issue here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/140813](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/140813)

Does this sequence which unloads and reloads the module help?

```

sudo ifdown eth0
sudo modprobe -r 3c59x
sudo modprobe 3c59x
sudo ifup eth0

```

---

### Post by Michl on 2007-10-15
WIll check that.  Just wanted to mention that it starts with detected link yes 
and it still doesn´t connect, and then it disconnects and the link switches to no
Michael

---

### Post by Michl on 2007-10-15
> **noob12 said:**
> The sudo lshw output is showing "link=no".  Assuming you've already checked cables and that it is plugged into an active port on the other side of the cable, this might be related to the issue here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/140813](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/140813)

Does this sequence which unloads and reloads the module help?

```

sudo ifdown eth0
sudo modprobe -r 3c59x
sudo modprobe 3c59x
sudo ifup eth0

```


That did it!  But I had to do it after the network was enabled.  If I did it
first, everything slowed down tremendously, e.g. opening the terminal
or networking.

Am I right to assume that I will have to do this everytime I boot-up, even
from Suspend?  (Last time what happened when I got it to work I think
I unloaded and reloaded somehow, then suspended the laptop, and when I
returned it didn't work.)

Anyway, thank you very much!!!  :smile:
Michael

---

### Post by noob12 on 2007-10-15
Alas, you may be hitting other bugs with the suspend and networking.

Yes.  I think you do have to reload it each time you reboot.

To automate, one of the following should work.  Try the first.  If that doesn't work, back out that change and try the second

**Try using pre-up lines first**

This is the preferable approach if it works

```

sudo gedit /etc/network/interfaces

```

Just below your **iface eth0** line add the following two lines:
```

pre-up modprobe -r 3c59x
pre-up modprobe 3c59x

```

Save and exit.  Do a full reboot and see if things just work after reboot.


If it does not work, then take out those two lines and try the next method

**Try using commands in /etc/rc.local instead**

```

sudo gedit /etc/rc.local

```

Put the commands
```

ifdown eth0
modprobe -r 3c59x
modprobe 3c59x
ifup eth0

```

after all the initial comment lines that begin with **#** and *before* the final **exit 0** line that you find already in the file.  Then see if that works after a normal reboot.

---

### Post by Michl on 2007-10-17
Adding the commands to /etc/network/interfaces doesn't work,
but adding the commands to rc.local works.  I had to add some
ethtool commands to turn off autoneg and set the speed to
10mB/s.  The only problem is that loading takes a long time,
but once it's up everything is ok.

M

---

### Post by noob12 on 2007-10-17
Your network will only become available at rc.local time in that case.  If you take the **auto eth0** out of /etc/network/interfaces your boot time may improve.   

You may have issues doing network mounts in fstab, but otherwise I think you will be ok.  Add yourself to the bug report; I think they want someone to test if Gutsy has the same issue.

---

