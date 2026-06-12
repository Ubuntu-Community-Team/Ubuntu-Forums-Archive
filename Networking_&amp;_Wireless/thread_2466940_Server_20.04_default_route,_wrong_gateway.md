---
title: "Server 20.04 default route, wrong gateway"
date: 2021-09-10
forum: Networking &amp; Wireless
---

### Post by r4d14n7 on 2021-09-10
I have an Ubuntu Server 20.04 (just the CLI, no GUI) running a Plex Media Server. It, and the rest of my devices, are connected to a FortiGate at its default IP address, 192.168.1.99. Every so often, Ubuntu automatically adds a default route through 192.168.1.1, effectively killing all Inet access on the server. When I delete this route, Inet access is restored. There is no 192.168.1.1 anywhere on my network. Server's IP address is 192.168.1.25.

Output from 'ip route':

default via 192.168.1.1 dev enp0s25 proto static
default via 192.168.1.99 dev enp0s25 proto dhcp src 192.168.1.25 metric 100
192.168.1.0/24 dev enp0s25 proto kernel scope link src 192.168.1.25
192.168.1.99 dev enp0s25 proto dhcp scope link src 192.168.1.25 metric 100

If I delete the first line with 'ip route del default via 192.168.1.1', it's removed from the list, Internet access is restored until roughly 24 hours later (haven't actually timed it). No reboots required to break it. Maybe I should just change the IP of my FortiGate to 192.168.1.1 and call it a day? That sounds like a can of worms.

More info:
I'm running a DHCP server on the FortiGate and reserving IPs based on MAC addresses for everything in the environment (Desktops, laptops, phones, tablets, IoT stuff).
There is only one NIC in the server. It is not used for any sort of traffic control. It is a media server that reads data from an SMB share on a Windows box (until I have time to migrate data).
I don't know a whole lot about routing tables and the like. Googling shows a whole bunch of what I consider to be conflicting information.

---

### Post by TheFu on 2021-09-10
There are 4 possibilities.
[LIST=1]
[*]netplan file is wrong - /etc/netplan/*yaml
[*]dhcp server is providing bogus information - I don't use dhcp on my servers after the first boot. Too hackable. Sure, lots of enterprises do this, but that doesn't mean it is a good idea.
[*]a script, somewhere, is setting the route - Since only you see this, it is likely a script you wrote or part of an uncommon package.
[*]a VPN setup/teardown could be leaving junk behind - people often forget to mention they are using/running a VPN for the first 10 posts.
[/LIST]

Eliminate each of those as possible issues.

---

### Post by r4d14n7 on 2021-09-12
Thanks for the reply!

Yep, it was the first one. I opened that file and it listed 192.168.1.1 as the gateway. Must be a default value? I did not configure it this way. Changed to 192.168.1.99 and everything is good.

---

