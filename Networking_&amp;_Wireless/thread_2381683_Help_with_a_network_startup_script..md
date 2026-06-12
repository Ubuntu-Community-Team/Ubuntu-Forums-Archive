---
title: "Help with a network startup script."
date: 2018-01-04
forum: Networking &amp; Wireless
---

### Post by mainemojo on 2018-01-04
I have a laptop located 3 hours away in another state.  I am the only one that uses it.  What I would like is a way so that after a reboot or powering up, it....


[LIST=1]
[*]Bring the network up with the last configuration
[*]Ping 8.8.8.8.  If successful, then do nothing.  Else, continue.
[*]Set interface ETH0 to IP 192.168.0.1 and configure DNS for private DNS servers.
[*]Ping 8.8.8.8.  If successful, then do nothing.  Else, continue.
[*]Set interface ETH0 to IP 1.1.1.1 (a public IP) and configure DNS for public DNS servers.
[*]Ping 8.8.8.8.  If successful, then do nothing.  Else, continue.
[*]Set interface ETH0 to DHCP and get DNS servers from DHCP.
[*]Ping 8.8.8.8.  If successful, then do nothing.  Else, continue.
[*]Resort to the last configuration.
[/LIST]

As of now, the system is using network-manager.  I'm assuming that I would have to stop it so I can use ifup/ifdown.  What is the best way to do this?

---

### Post by TheFu on 2018-01-04
Purge network manager stuff. Then create the script that does whatever you want.

However, with 16.04 and later, ethernet device names are fairly unique. No more eth0.

Personally, I'd just have a set config in /etc/network/interfaces for each of the possible cases, then copy the one I wanted based on the situation/location and restart networking.

BTW, I'd just try with DHCP first. If that didn't get the correct/expected subnet/IP, then I'd copy the static config into place and restart networking.

You should put a maximum tries limiter into your script.  Having the same thing fail for 5 weeks in a tight loop isn't helping anyone. I'd probably try once an hour, if things weren't working.

Under 17.10, there's a new method for network configs, the "interfaces" file isn't used anymore.

So ... the first question you need to answer is which release will be running?

---

