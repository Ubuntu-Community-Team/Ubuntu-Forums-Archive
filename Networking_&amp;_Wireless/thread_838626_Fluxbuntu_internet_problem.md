---
title: "Fluxbuntu internet problem"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by Niila on 2008-06-23
I have buffalo g54 wi-fi card using bcm43xx firmware. All the lights are lit up and network configurator finds my essid, but it doesnt connect.

I also have intel pro/1000 mt network card, which also seems to be recognized, but no connection here either. 

Heres what the network configurator says:

```
Configuring device eth1 :

$ iwconfig eth1 essid "dd-wrt"

$ iwconfig eth1 rate auto

$ iwconfig eth1 key XXX...

$ pkill -9 wpa_supplicant

$ wpa_supplicant -Bw -Dndiswrapper -ieth1 -c/etc/wpa_supplicant/wpa_psk.conf

$ ifconfig eth1 up

DHCP may take a while, please wait...
$ dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 4914
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:16:01:7b:a8:5e
Sending on   LPF/eth1/00:16:01:7b:a8:5e
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Configuring device eth0 :

$ ifconfig eth0 up

DHCP may take a while, please wait...
$ dhclient eth0

```

I tried to install wifi-radar but fluxbuntu doesnt open .dep files.

Help :confused:

---

### Post by dmizer on 2008-06-23
fluxbuntu is a very light gui, and as a result, you will end up doing many things in the command line.

to install a deb via command line, use this command:
```
sudo dpkg -i package.deb
```
suggest staying away from wifi-radar or any other wireless utility you can't get via the regular package system.

first of all, post the output of:
```
lshw -C network
```
with the information from that command, we can configure your network settings without guessing.

---

### Post by Niila on 2008-06-24
Thanks!

Im just thinking, how hard would it be to execute automatically that kind of simple command when i click the deb file..

Anyhow, heres the output before i clicked "apply" from the network config.

```

  *-network DISABLED      
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0d:60:77:26:f0
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-f
d 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversio
n=7.3.20-k2-NAPI firmware=N/A latency=64 link=no mingnt=255 module=e1000 multica
st=yes port=twisted pair
  *-network DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:16:01:7b:a8:5e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-gener
ic latency=64 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

```


And heres after:

```
     *-network               
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0d:60:77:26:f0
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-f
d 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversio
n=7.3.20-k2-NAPI firmware=N/A latency=64 link=no mingnt=255 module=e1000 multica
st=yes port=twisted pair
  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:16:01:7b:a8:5e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-gener
ic latency=64 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

```

---

### Post by dmizer on 2008-06-24
again, the whole point of fluxbuntu is to be light.  people who make use of fluxbuntu generally do so because they do not need all the fancy looking gui front ends in order to efficiently accomplish simple tasks like installing a debian package.

well, you appear to be enabling both your wired and your wireless interface.  that could be part of your problem.  you can have one or the other, but not both.

please post the contents of:
/etc/network/interfaces

---

### Post by Niila on 2008-06-25
I think "light-weight" is just an excuse for not having easy-to-use interface, even without fancy gui.

Heres my interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

```

Ive tried having only one enabled, didnt have an effect.

---

### Post by dmizer on 2008-06-25
> **Niila said:**
> I think "light-weight" is just an excuse for not having easy-to-use interface, even without fancy gui.
while this is true to some extent, fluxbox is intended to be extremely minimalistic.  the main focus of fluxbox is in how it handles windows, not in how easily you can set up your network.  more information here: [http://fluxbox.org/features/](http://fluxbox.org/features/)

if you want a window manager that is designed to be both lightweight and uses a point-and-click interface, you'll probably prefer xfce.  but fluxbox is definately not a point-and-click user interface.

> **Niila said:**
> Heres my interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

```

Ive tried having only one enabled, didnt have a effect.

okay, in your interfaces file, you'll just need to add lines for your network adapters.  decide which one you want as your primary interface (wireless or wired) and set them up like so:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# Wired network interface
iface eth0 inet dhcp

# Wireless network interface
iface eth1 inet dhcp
wireless-essid XXX-essid-here-XXX
wireless-key xxx-wep-key-in-hex-xxx

# Bring this interface up on boot
auto eth0
```
if you want your wireless card to be connected at boot, change "auto eth0" to "auto eth1"

---

### Post by avalenc on 2008-10-22
So, how do I get to see the interfaces list?

I don't know where to get to the /etc/.../interfaces list, nor do I know what command to use.

Is is correct that first I install ndiswrapper, then a driver, and then somehow configure/add eth1? 

Please pardon my total ignorance, as I'm fairly new to CLIs. Thanks!

---

### Post by snowpine on 2008-10-22
In Fluxbuntu, you can set the default behavior for a file type by right clicking and choosing "Set Run Action." So, right click on a .deb file, choose Set Run Action, and type 'sudo dpkg -i' to make it "user friendly" by your definition. :)

(edit)Fluxbuntu does not assign default applications to different file types. It lets *you* decide which applications you want to use as the defaults. So there is a little bit of a "learning curve" while Fluxbuntu learns which apps you want to use. You have to understand and agree with the "Fluxbuntu philosophy" if you're going to have a positive experience--it's a little different from most other distros in that regard.

---

