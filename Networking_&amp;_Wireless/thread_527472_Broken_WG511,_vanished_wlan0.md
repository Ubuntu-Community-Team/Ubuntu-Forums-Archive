---
title: "Broken WG511, vanished wlan0"
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by aasmith on 2007-08-16
Any help would be most welcome--I'm very frustrated with this right now.  (Please note that I don't know the inner workings of Ubuntu, so please explain any commands you have me run, and what they do.)

I have a WG511 card.  (I believe it's v1.)  It was working fine until yesterday.  Then it died, and I can't even get the lights on it to blink.

It's been kinda weird on me for a while--for example, as long as I was running Dapper, I had interfaces named eth0, eth1, and eth2.  eth0 was wired, and eth1 and eth2 were both wireless, but only one would work.  Which one seemed to be randomly selected at bootup.  When I upgraded to Feisty, eth1 and eth2 were replaced by wlan0.

Yesterday I completed a cross-country move, and was setting up my wireless.  (It's thus conceivable that some bit of hardware got broken in the move.)  Since my networking situation is not finalized, I selected the "roaming mode" option in the networking setup to see what it did--it just erased some of my setup info, and didn't work.  Had to reenter some data when I switched back--for example that I wanted to use DHCP.  But from then on nothing worked, and wlan0 totally vanished from my interfaces.  I have an eth1, but it's totally unusable--it doesn't see any networks in the area, and seems to be permanently disabled.

Could someone *please* help?  Outputs of some diagnostics follow the body of this message.

Thank you,
Adam

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"s"  Nickname:"ssid"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:38:17:82:EC  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:38ff:fe17:82ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:6611 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5812 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4632763 (4.4 MiB)  TX bytes:1066635 (1.0 MiB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

$ ndiswrapper -l
netwg511 : driver installed

---

### Post by kevdog on 2007-08-16
Can you post the following:
lshw -C network
/etc/iftab
/etc/network/interfaces

Thanks

---

### Post by aasmith on 2007-08-16
Note--bcgmscfloor6 and tsunami are both names of networks to which I've connected in the past.

Thanks.

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 DISABLED    
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@02:04.0
       logical name: eth1
       version: 03
       serial: 00:14:a5:10:3e:6d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-386 latency=64 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:d0000000-d0001fff irq:22
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@02:0e.0
       logical name: eth0
       version: 02
       serial: 00:14:38:17:82:ec
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=192.168.1.102 latency=64 multicast=yes
       resources: iomemory:d0008000-d0009fff irq:21

$ cat /etc/iftab
# This file assigns persistent names to network interfaces.  See iftab(5).
eth0 mac 00:14:38:17:82:ec
ethX mac 00:09:5b:e8:cb:80

$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.

iface eth2 inet dhcp
wireless-essid linksys

iface eth3 inet dhcp
wireless-essid bcgmscfloor6

auto eth3

iface ethX inet dhcp
wireless-essid tsunami

iface wlan0 inet dhcp
wireless-essid linksys

iface eth0 inet dhcp

auto eth0

iface eth1 inet dhcp
wireless-essid linksys

---

### Post by kevdog on 2007-08-16
Wow- you are trying to do a bunch of different things.

Here is what I would do.

Make the following modifications to your /etc/iftab file
gksu gedit /etc/iftab

Put a # sign infront of the ethx line, add the following:

wlan0 mac 00:14:a5:10:3e:6d arp 1


Next back up your /etc/network/interfaces file
sudo /etc/network/interfaces /etc/network/interfaces.bak

Edit your /etc/network/interfaces file to have only the following (gksu gedit /etc/network/interfaces):
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.

auto eth0
iface eth0 inet dhcp

auto wlan0 
iface wlan0 inet dhcp
wireless-essid linksys


Make sure linksys is the essid you want to associate with using the wlan0 or wireless card
Id reboot at this point.

---

