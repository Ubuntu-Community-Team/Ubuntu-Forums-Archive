---
title: "running Ubuntu as a firewall/gateway/NAT/DHCP server"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by boondocks on 2007-10-21
I have a PC running Ubuntu 7.10 and it has 2 ethernet PCI cards.
I have a broadband connection.

I want this Ubuntu PC to be the firewall/gateway/NAT/DHCP server running Tor/Privoxy where:
[LIST]
[*]eth0 connects to the WAN = internet
[*]eth1 connects to the LAN = 192.168.10.x where eth1 would actually be 192.168.10.1
[/LIST]
On the LAN, there are about 20 DHCP clients like:
[LIST]
[*]PCs
[*]Network storage appliance
[*]Motion sensor Camera
[*]Heating and Cooling equipment
[*]etc.
[/LIST]
These DHCP clients cannot be forced to work with a socks proxy.

But I want all internet access originating from these clients, to travel via this Ubuntu system.
I want Tor to listen on the 192.168.10.1 interface.
So this Ubuntu system should be more than just an optional proxy.

How do I configure this Ubuntu system to do this job?
Can you point me to some kind of checklist to do this?

---

### Post by jim_naisium on 2007-10-23
I am trying to set up the exact same thing, I was able to do it with Slackware (which is currently running the network) but the config files are different for Ubuntu so I can't port everything over to Ubuntu.

---

