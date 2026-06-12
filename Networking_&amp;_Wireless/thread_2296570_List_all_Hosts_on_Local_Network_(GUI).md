---
title: "List all Hosts on Local Network (GUI)"
date: 2015-09-26
forum: Networking &amp; Wireless
---

### Post by Jason_Hunter on 2015-09-26
I'm well versed in port scanning and nmap and all and it's not what I'm looking for. 

I just want to see all hosts on my local network, like where is my printer?

I have no problem to scan my network and I have no problem to look in dhcpd releases file, but it's not quick enough. 

Don't we have some kind of simple GUI app that just shows everything that is on the network?

I don't want a GUI port scanner where I punch in an nmap command and then wait until it has scanned the network. 

I want something that continually keeps an eye open and sees what's going on on the network. 

Like, click on a network icon and just see what's there?

---

### Post by TheFu on 2015-09-26
That isn't IPv4 how networking works, as you already know. IPv6 can do it because arp is built into the protocol.
**arp** is the closest thing for what you want, but it doesn't provide IPs and may not provide the hostname you expect/want.  Plus arp only works over ethernet, not IP. Beyond the subnet - no way to know what is out there with arp.

So ... you have a choice to make.
a) learn about zeroconf and buy into that 100% with some unsupported devices.
    [https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf)
b) manually manage your network with static IPs for everything and maintain the /etc/hosts file
    [http://blog.jdpfu.com/pages/hosts-for-security](http://blog.jdpfu.com/pages/hosts-for-security)
c) setup DHCP reservations for every device, assuming the network router can do that AND be a local DNS server too.
    [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)

I use "b" and a little "c" (for portable devices only).
I've been screwed by "a" to the point that purging those tools is part of my normal system install process. I purge nano and network-manager too. ;)

I don't know of any GUI besides Zenmap for this stuff.  You could run nmap every few hours and put the output into an html file by using cron. [https://nmap.org/book/output-formats-output-to-html.html](https://nmap.org/book/output-formats-output-to-html.html)

Not certain that I understand the point of this.  Perhaps if you explain the end-goal, we can provide a better solution?

---

