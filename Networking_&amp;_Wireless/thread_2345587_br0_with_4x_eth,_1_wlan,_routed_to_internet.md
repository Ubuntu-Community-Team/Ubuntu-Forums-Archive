---
title: "br0 with 4x eth, 1 wlan, routed to internet"
date: 2016-12-05
forum: Networking &amp; Wireless
---

### Post by darren780 on 2016-12-05
```
Linux xxx 4.8.0-28-generic #30-Ubuntu SMP Fri Nov 11 14:03:52 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

This is what I have made, but cannot get ubuntu to boot up as such, maybe this is not the correct way to do things?
```

bridge name    bridge id        STP enabled    interfaces
br0        8000.00xxxxxxxx14    no        eth0
                            eth1
                            eth2
                            eth3
                            wlan0

```

I am using hostapd for the wlan0 interface and br0 for bridge, relevant parts:
```

interface=wlan0
bridge=br0

```

startup programs keep fighting me by renaming by br0 to rename7, rename9.  
```

bridge name    bridge id        STP enabled    interfaces
br0        8000.00xxxxxxxx17    no        eth3
rename7        8000.00xxxxxxxx14    no        eth0
                            eth1
rename9        8000.00xxxxxxxx16    no        eth2

```


my /etc/network/interfaces file
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto net0
allow-hotplug net0
iface net0 inet dhcp

auto wlan0
allow-hotplug wlan0
iface wlan0 inet manual

auto br0
iface br0 inet static
        bridge_ports wlan0
        address 192.168.1.1
        network 192.168.1.0
        netmask 255.255.255.0
        gateway 192.168.1.1
        broadcast 192.168.1.255
        bridge_maxwait 0
        allow-hotplug br0

```

I have tried ```
bridge_ports all
``` and ```
bridge_ports eth0 eth1 eth2 eth3
``` Does not seem to boot well when adding wlan0 at this stage.

At current I have to run these commands after bootup, but should it not be done in /etc/network/interfaces ?
```

brctl addif br0 eth0
brctl addif br0 eth1
brctl addif br0 eth2
brctl addif br0 eth3
ifconfig eth0 up
ifconfig eth1 up
ifconfig eth2 up
ifconfig eth3 up

```

---

### Post by darren780 on 2016-12-08
Discovered another method to use bridge_ports
        ```
bridge_ports regex (eth|wlan).*
```

This is the result:
```

bridge name    bridge id        STP enabled    interfaces
br0        8000.00xxxxxxxx15    no        eth1
                            eth2
                            wlan0
rename7        8000.00xxxxxxxx14    no        eth0
rename9        8000.00xxxxxxxx17    no        eth3

```
Why can it not add eth0 and eth3 to br0 from interfaces?

---

### Post by Bashing-om on 2016-12-08
darren780; Hey ;

As i pass by;
A thought:
As booting "4.8.0-28-generic" then this is  systemd and as such the nomenclature of the networking devices are changed:
see: [https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)

[INDENT][INDENT][INDENT]hope this helps
[/INDENT][/INDENT][/INDENT]

---

### Post by darren780 on 2016-12-09
Thank you for the tip  Bashing-om. 
I can report success.  
/etc/network/interfaces(only relevant part):
    ```
bridge_ports regex (wlan|eth).*
```

I have removed /etc/udev/rules.d/10-network.rules and replaced it with these files.

/etc/systemd/network/10-eth0.link:
```

[Match]
Driver=e1000e
MACAddress=xx:xx:xx:xx:xx:14

[Link]
Name=eth0

```

/etc/systemd/network/11-eth1.link:
```

[Match]
Driver=e1000e
MACAddress=xx:xx:xx:xx:xx:15

[Link]
Name=eth1

```

/etc/systemd/network/12-eth2.link:
```

[Match]
Driver=e1000e
MACAddress=xx:xx:xx:xx:xx:16

[Link]
Name=eth2

```

/etc/systemd/network/13-eth3.link:
```

[Match]
Driver=e1000e
MACAddress=xx:xx:xx:xx:xx:17

[Link]
Name=eth3

```

/etc/systemd/network/20-net0.link:
```

[Match]
Driver=r8169
MACAddress=xx:xx:xx:xx:xx:49

[Link]
Name=net0

```

```
[Match]
MACAddress=xx:xx:xx:xx:xx:18
Driver=ath9k

[Link]
Name=wlan0

```

And this one to help prevent renaming while creating the bridge
/etc/systemd/network/30-br0.link:
```
[Match]
Driver=bridge

[Link]
Name=br0

```
Beware, 30-br0.link could cause trouble if you have more than one bridge.

---

### Post by Bashing-om on 2016-12-09
darren780; :)

You do good work . Appreciate that ya gave your solution .

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by darren780 on 2016-12-09
Followup, I removed 30-br0.link and continue to have no further renaming issues. 
/etc/systemd/network/30-br0.link:
```
[Match]
Driver=bridge

[Link]
Name=br0

```

I am going to guess that the renaming of br0 to rename7, rename9, etc was caused by renaming based on mac address.  br0 obviously has the same mac as one of the adapters.
Here is my original(deleted) /etc/udev/rules.d/10-network.rules which I created following tutorials:
```

SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="xx:xx:xx:xx:xx:49", NAME="net0"
SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="xx:xx:xx:xx:xx:18", NAME="wlan0"
SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="xx:xx:xx:xx:xx:14", NAME="eth0"
SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="xx:xx:xx:xx:xx:15", NAME="eth1"
SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="xx:xx:xx:xx:xx:16", NAME="eth2"
SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="xx:xx:xx:xx:xx:17", NAME="eth3"

```

---

