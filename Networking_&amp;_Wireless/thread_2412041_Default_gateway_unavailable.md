---
title: "Default gateway unavailable"
date: 2019-02-07
forum: Networking &amp; Wireless
---

### Post by nickp666 on 2019-02-07
Hello

I've got a server running 14.04.3 LTS.  Up until recently the machine has been operational without any issue.  I tried to login to the machine remotely yesterday but it was offline.  From the console everything seems to be OK.  I can ping devices on the same subnet as the server but everything else including the default gateway are unresponsive, 96-100% packet loss.  I've checked the IP configuration of the NIC and this looks correct.  Details below:

auto em4
iface em4 inet static
address 192.168.240.105
netmask 255.255.255.0
gateway 192.168.240.254

This is the same configuration as other devices in this subnet and these machines are still live on the network and remotely available.  I've change the switch port the server is connected to and also moved the sever to another LAN switch but I get the same results.  If I change the NIC config to DHCP and drop the switch port into a different VLAN the server picks up a new IP address and everything is OK.  Change the config to static with the same IP address as the DHCP config and again everything is OK. I only seem to have a problem with the 192.168.240.0 network. 

Can anyone shed any light as to what I should be look at as I'm at a complete loss. 

Thanks

---

### Post by TheFu on 2019-02-07
LAN port issue?

You didn't mention if this was a physical or virtual server.  There have been issues with virtio for 14.04 systems.  I had a single VM stop all internet access, but retain LAN access for about a day a few times.  Moved that VM to a different VM host and it has been working fine.  The 1st VM host has 10 other VMs, with the same OS, on the same bridge, that never showed any issues at all.

Anything useful in any logs?

But really, 14.04 is EOL in 2 months, so it is time to move to a newer release. You aren't alone.  At this point, I'd just move to a newer release.

---

