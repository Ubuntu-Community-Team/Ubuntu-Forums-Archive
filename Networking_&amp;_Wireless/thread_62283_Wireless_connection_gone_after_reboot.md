---
title: "Wireless connection gone after reboot"
date: 2005-09-04
forum: Networking &amp; Wireless
---

### Post by benash on 2005-09-04
My RT2500-based wireless card loses connectivity after I reboot.  I can get it working if I do:

> sudo ifdown ra0
sudo ifup ra0
^c
sudo ifup ra0
^c
sudo ifup ra0

I don't know why it takes 3 ifup's for it to work.  Here is my /etc/network/interfaces, which I think was modified by the System>Administration>Networking tool:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0


iface ra0 inet dhcp
wireless-essid New
wireless-key aaaaaaaaaaaaaaaaaaaaaaaaaa

auto ra0


Thanks for any consideration,
Ben

---

### Post by joepotter on 2005-09-04
[QUOTE=benash]My RT2500-based wireless card loses connectivity after I reboot.  I can get it working if I do:



I don't know why it takes 3 ifup's for it to work.  Here is my /etc/network/interfaces, which I think was modified by the System>Administration>Networking tool:



Thanks for any consideration,
Ben[/QUOTE]

Your interfaces file looks just like several I have at work except that I commented out the eth0 (#   map eth0 ). But that should not be your troubles.

I would boot the computer and then check iwconfig, ifconfig, lspci, and lsmod to see what the state is. 

I once had similar troubles but it was a problem with dhcp3 rather than with the card. I went static and all started working; so I knew I had dhcp problems --- they went away on upgrade.

Good luck.

---

### Post by benash on 2005-09-05
I used iwconfig to discover that at boot-up, the card connects to some other network:

> 
ra0       RT2500 Wireless  ESSID:"changhun"  
          Mode:Managed  Frequency=24.62 MHz  Access Point: 00:30:BD:FD:21:3B   
          Bit Rate:54 Mb/s   
          RTS thr: off   Fragment thr: off
          Link Quality=68/100  Signal level=-78 dBm  Noise level:-206 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



Apparently it tries to connect to networks other than the ones in interfaces?

---

### Post by benash on 2005-09-06
Fixed . . .

I started over and followed the instructions in the README, instead of the How-to.  I'm not sure what made the difference, though.  This time I created /etc/sysconfig/network-scripts/ifcfg-ra0 and /etc/Wireless/RT2500STA/RT2500STA.dat, and I know I didn't do that before.

Ben

---

### Post by joepotter on 2005-09-10
[QUOTE=benash]Fixed . . .

I started over and followed the instructions in the README, instead of the How-to.  I'm not sure what made the difference, though.  This time I created /etc/sysconfig/network-scripts/ifcfg-ra0 and /etc/Wireless/RT2500STA/RT2500STA.dat, and I know I didn't do that before.

Ben[/QUOTE]

I am glad you got it going.

You will love the new Breezy as it supports rt2500 chips out of the box.

Have fun.

---

