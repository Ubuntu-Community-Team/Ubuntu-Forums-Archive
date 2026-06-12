---
title: "Is it possible to bridge ethernet ports like a switch?"
date: 2020-06-28
forum: Networking &amp; Wireless
---

### Post by dazmatic on 2020-06-28
Fresh install of 20.04 on a newly built machine with old parts. G1840, H81 motherboard, 4 port pcie ethernet card + 1* built in port.
I've got a nas, PX4-300D and I'm planning on using this new machine as a pi-hole, owncloud and plex server.  
I'm looking to use all the ethernet ports as a bit of a switch. The NAS has bonded ethernet ports for a total of 2gbit.

Is it possible to set up all 5 ports as a bridge so that 1 port feeds into the machine from the local network and 2 of them feed in from the NAS? My VDSL modem router handles all the DHCP networking.

So it'll look like: 
Router --> Powerline network --> machine <--> NAS

I kind of got it working manualy via the CLI and brctl utils and restarted the machine and it all broke. 

I'm a novice with Ubuntu but understand it's an incredibly useful tool but there's so much to learn.

---

### Post by Tadaen_Sylvermane on 2020-06-29
So according to the debian wiki this can be done with a regular bridge. Ubuntu however uses netplan. So you will need to create a configuration file for it to read. Config file in /etc/netplan/
Do not use this file verbatim. It won't work. Needs to be custom to your interface names.

Something like this maybe?

```
network
 version: 2
 renderer: networkd
 ethernets:
  eth0:
   dhcp4: false
  eth1:
   dhcp4: false
  eth2:
   dhcp4: false
  eth3:
   dhcp4: false
 bridges:
  br0:
   interfaces: [eth0, eth1, eth2, eth3]
   dhcp4: false
```

I have no way to test this. I am curious if it will work but to be honest, gigabit switches are so cheap these days this may just not be worth it.

---

### Post by dazmatic on 2020-06-30
Thanks for the assist.

Your exactly right, using netplan with the configuration like that works really well.

I've got spare switches, but, I didn't want to have another device just laying about. 

The issue now comes in when installing pihole. I've got nginx installed as part of an owncloud install and that uses port 80.

Pihole uses port 80 also so when pihole is installed there's no connectivity any more because the DNS fails to get a response on port 80. If I change the port to say 8080 it still doesn't work but possibly because I haven't opened that port manually?

If I unplug an replug the Ethernet connection from the router, I get connectivity for about half a second before it's gone again. 

Just been looking into pihole with docker and reverse proxy so that I can use nginx as a webserver for owncloud

---

