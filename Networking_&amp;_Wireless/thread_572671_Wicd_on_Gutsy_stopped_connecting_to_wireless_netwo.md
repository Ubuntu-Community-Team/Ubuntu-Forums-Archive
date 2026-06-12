---
title: "Wicd on Gutsy stopped connecting to wireless networks"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by jonathanmotes on 2007-10-10
I installed Wicd on Gutsy (after removing network-manager and network-manager-gnome) when I started having trouble connecting to the wireless at school. It turned out they were having network problems. Now they seem to have the networking issues fixed (it works when I boot Vista), but after using Wicd flawlessy for two days, it has mysteriously stopped connecting to wireless networks (it still works for wired connections). Does anyone have any ideas on how to fix this? I suppose the updates could have broken something.

Thanks!

EDIT: I figured out half of the problem: "network settings" shows that my wireless has been disabled, but I can't figure out how to change it back to roaming mode. My only options seem to be to set it up manually to connect to a single network.

Here's my network configuration file from /etc/network/interfaces:```
auto lo
iface lo inet loopback

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp







#iface eth0 inet dhcp

#auto eth0
```

Does anyone know of a way to manually configure this?

---

### Post by jonathanmotes on 2007-10-10
Anyone?

---

### Post by kevdog on 2007-10-10
Lets just troubleshoot your connection first.  There is a link at the bottom of this post in my signature that gives instructions how to connect manually.  If you can do this, then we can modify the interfaces file appropriately.

---

### Post by jonathanmotes on 2007-10-10
Thanks for responding!

I seem to be having some problems. Here's my output from lshw -C network```
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:63:8f:02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

Here's the output when trying to connect to a Unencrypted Connection:

```
jmotes1@jmotes1-laptop:~$ sudo ifconfig wlan0  down
jmotes1@jmotes1-laptop:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1a:73:63:8f:02
Sending on   LPF/wlan0/00:1a:73:63:8f:02
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 1.1.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
jmotes1@jmotes1-laptop:~$ sudo ifconfig wlan0 up
jmotes1@jmotes1-laptop:~$ sudo iwconfig wlan0 essid "HUWA-GUEST"
jmotes1@jmotes1-laptop:~$ sudo iwconfig wlan0 mode Managed
jmotes1@jmotes1-laptop:~$ dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted

```

I was able to connect manually to a network using "Network settings" before trying this. I disconnected from the network using Wicd before proceeding with the above.

I need to be able to connect to a WPA2 networks and wired connections also if that helps you figure out what I need.

Thanks again for helping me. I may not be able to correspond after a few minutes until sometime tomorrow.

---

### Post by kevdog on 2007-10-10
Its

sudo dhclient wlan0

---

### Post by bapoumba on 2007-10-10
In /etc/network/interface, I'd uncomment the iface line corresponding to the device for you card.

---

### Post by jonathanmotes on 2007-10-10
> Its

sudo dhclient wlan0OK, here's the output now:```
jmotes1@jmotes1-laptop:~$ sudo dhclient wlan0
[sudo] password for jmotes1:
There is already a pid file /var/run/dhclient.pid with pid 12758
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1a:73:63:8f:02
Sending on   LPF/wlan0/00:1a:73:63:8f:02
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 1.1.1.1
bound to 10.3.5.189 -- renewal in 345499 seconds.

```

It seems to work! I am connected...

---

### Post by jonathanmotes on 2007-10-10
> In /etc/network/interface, I'd uncomment the iface line corresponding to the device for you card.OK...I will continue working on this tomorrow! Thanks for your help!

---

### Post by kevdog on 2007-10-10
report back tomorrow and we can finish things up!!

---

### Post by bapoumba on 2007-10-11
Hello, and I'm sorry, I have not much time right now.

```
auto wlan0
iface wlan0 inet dhcp
```

I understand wlan0 Is your wireless device, am I right ?
The corresponding /etc/network/interface shoud at least look like this.

Here is mine for comparison:
```
# Wifi maison
iface wlan0 inet dhcp
wireless-essid <insert_your_network_here>
wireless-key <insert_your_key_here>
auto wlan0
```
Your network is HUWA-GUEST.
Is this an open network? If so, you do not need the line "wireless-key".

So change the file, and restart the networking services:
```
sudo /etc/init.d/networking restart
```
And paste the output, along with the output to:
```
iwconfig
```

---

### Post by jonathanmotes on 2007-10-11
> In /etc/network/interface, I'd uncomment the iface line corresponding to the device for you card.OK, uncommenting "iface wlan0 inet dhcp" and commenting out "wireless-essid HUWA-GUEST" (which I think was added when creating a manual connection with the terminal) is  working for unsecured connections. Thanks!! 

Also, I need to connect to a secure network, which shows up as WPA2 in Wicd. The problem is (which I should have researched before installing Wicd) is that my school does not give me the key. I have to use my user name and password to be able to connect. With the Network-Manager, I was able to do this by entering random numbers for the password (which is the key). This gave me another window (see attachment) that allowed me to enter my school user name and password. Do you know of a solution to this?

Oh, I almost forgot....Do you know why my "network settings" program does not show "roaming mode" anymore? Was this a function of the "network-manager" that I uninstalled?

Another question: I once commented out some of the things in this file (that is probably why the line "iface wlan0 inet dhcp" was) because a post on the forums said that would help my computer boot faster. I tried to restore it back to normal, but I wasn't sure which lines I had commented, because I seem to recall that some of them were already. Do you know the normal configuration - as far as the comments go? 

Also, to bapoumba, I think my configuration is similar to yours now. But I don't want to have to include the essid, since I want to have a sort of "roaming"ability. Also, thanks for showing me how to restart the connection after editing the file. That was very helpful!

Thanks!

---

