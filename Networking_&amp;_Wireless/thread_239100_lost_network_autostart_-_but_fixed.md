---
title: "lost network autostart - but fixed"
date: 2006-08-18
forum: Networking &amp; Wireless
---

### Post by anopheles on 2006-08-18
Summary: got into a position where networking doesn't start at boot time but can be started manually. 
Suspect: NetworkSettings tool can mangle its config file.

Fixed it. I've seen several other threads discussing failed network autostart; this might be related, so perhaps my fix or observations could be useful.
-----

Tonight I was testing a friend's ADSL router whose default address was 192.whatever. My normal router is at 10.0.0.138 so I decided to leave the new router alone and change my IP address.

I used the K/SystemSettings/NetworkSettings tool to change my workstation address to 192.168.1.32. No obvious problem - I could talk to the router and set it up, but although it started my ADSL connection to the net, I couldn't see anything outside my LAN. 

After some messing about I decided to revert my workstation to its previous IP - 10.0.0.32 - and reconfigure the router to match - but the NetworkSettings tool refused to play ball. It would accept the 10.0.0.32 address (on eth0) but then immediately disable eth0. 

I rebooted as part of trying to fix this, and noticed that networking failed to start. 

However, I could start it manually with:
ifconfig lo 127.0.0.1
ifconfig eth0 10.0.0.32 up
route add default gw 10.0.0.138

---------
I've finally discovered something has mangled my /etc/network/interfaces file. I suspect the NetworkSettings tool ... (I might have done *something* stupid, but I dont think the tool should leave a garbage config file)

The file had become:
[INDENT]
# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        ***address 10.0.0.138***
        netmask 255.0.0.0
        network 10.0.0.0
        broadcast 10.255.255.255
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 10.0.0.138
        dns-search jupiter.sol

***iface eth1 inet***

auto eth0
[/INDENT]


The command ifup barfs at the line 'iface eth1 inet', which is incomplete. 
Yes, I do have two ethernet interfaces, but I had the second marked as "disabled".

Also: the address given for eth0 10.0.0.138 is the address of my router, should be the address of my workstation - 10.0.0.32, 
AND there is no gateway information.

I vi'd the file manually, and it now works. Final version:
[INDENT]
# The loopback network interface
***auto lo eth0***
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        ***address 10.0.0.32***
        netmask 255.0.0.0
        network 10.0.0.0
        ***gateway 10.0.0.138***
        broadcast 10.255.255.255
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 10.0.0.138
        dns-search jupiter.sol

***iface eth1 inet dhcp***
[/INDENT]

Forgive the hack: I set eth1 to dhcp just to put some sort of valid syntax in there - I haven't really studied all the rules for this file. Could I just leave eth1 out?

Tip: if "/etc/init.d/networking start" isn't playing ball, then run
ifup -v -i /etc/network/interfaces -a
and look for warning messages on STDERR.

Anyone know what NetworkSettings might have been doing to the interfaces file?

---

