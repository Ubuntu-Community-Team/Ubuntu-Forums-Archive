---
title: "WPA in Network Manager"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by Mad-Halfling on 2007-09-08
How much joy have people had getting WPA-PSK working in Ubuntu 7.04?

The situation I am in is I have a WPA-PSK wireless at home and a WEP network at my girlfriend's and I move regularly between them so I need to be able to flick between profiles easily.  I have got the WEP network connecting fine using gnome network manager but I can't get the WPA-PSK to appear in the "password type" when setting up a network profile.  I can see the network when doing a roaming connection, and seem to be able to connect (though as I have static IPs, I can't get a full connection).  I have tried using wicd but can't get much joy on that (it connects hits about 77%, then about 59% then drops to 0 and I can't ping my router).

Help, this is stopping me using Linux and I might have to go back to windows if I can't get it fixed  =8(

I know my card supports the setup (hardware-wise) as it works fine in windows.

I have an HP Pavillion dv6000 and lshw -C network shows the N/W H/W as:-
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth1
       version: 02
       serial: 00:19:d2:50:12:24
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 link=no multicast=yes wireless=unassociated
       resources: iomemory:d8000000-d8000fff irq:16
  *-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth0
       version: 00
       serial: 00:16:36:e8:3a:6c
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI duplex=half firmware=0.5-1 ip=10.1.8.6 latency=0 link=yes multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:da000000-da01ffff ioport:4000-401f irq:18

Anyone got any light they can shed on this?  Is network manager bugged WRT using WPA in the password type drop-down, or is there a way I can set this up/enable this?

Cheers

MH

---

### Post by jimbob on 2007-09-08
As a start I would recommend getting rid of Network Manager and installing Wicd.  It is a much better network manager IMHO and can handle WPA1/2 perfectly.  If I remember correctly when you install it, it will remove the Gnome network manager automatically.  You can always re-install it again if you want to go back.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Mad-Halfling on 2007-09-10
As I mentioned, I already tried that, it seems to connect and then drops.  Has anyone else had this problem?  Plus it doesn't seem to always refresh the connections list properly (though I only tried it briefly) and didn't show my home network when the SSID was hidden which meant I had to enter my SSID to get the settings.

On a personal note, I think the NM actually gives me what I want in a more convenient interface, but I'm happy to use anything that works.....

---

### Post by jimbob on 2007-09-10
Some people have had success with Wifi-radar, have you tried that?

I don't understand when you say "hits 77%, then 59%, then 0".  Are you talking about signal strength?  If the signal strength varies that much and you are not moving around maybe you have a problem with your radio chip or antenna.

---

### Post by Mad-Halfling on 2007-09-11
I am stationary, and when I authenticate with the WPA-PSK the signal strength/connection seems to go up, then drop back down in about 5 secs to 0%.  The hardware is fine as I can get the connection to the wireless working fine in windows.  I'll try wifi-radar, thx

---

