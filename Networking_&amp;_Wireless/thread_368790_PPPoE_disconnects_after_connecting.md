---
title: "PPPoE disconnects after connecting"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by elii on 2007-02-23
I only recently moved to Ubuntu 6.10, and I have a problem with my PPPoE ADSL connection. It sets up easily, works and connects to the Internet but after about 20 minutes I can no longer connect to the Internet.
Strangely enough, a download will continue to download even when Firefox doesn't work. This might be a DNS problem of some sort, as existing connections are mentained.

I'm using a PPPoE ADSL with dynamic IP address and dynamic DNS (I don't know any IP when connecting).
From the logs, I think this might be useful (if the entire log is needed, I'll post it):

Feb 24 01:07:58 elii pppd[9560]: Plugin rp-pppoe.so loaded.
(here is the connection and IPs)...
Feb 24 01:08:18 elii pppd[9485]: Timeout waiting for PADS packets
Feb 24 01:08:18 elii pppd[9485]: Terminating on signal 15
Feb 24 01:08:18 elii pppd[9485]: Exit.

I think that the last three lines of the pppd log might point to the problem.

Also, around the same time I lose conenction to the Internet, several daemon log lines appear:
Feb 24 01:23:11 elii dhclient: DHCPREQUEST on eth0 to 10.x.x.x port xxx
Feb 24 01:23:11 elii dhclient: DHCPACK from 10.x.x.x
Feb 24 01:23:11 elii dhclient: bound to 10.x.x.x -- renewal in 1651 seconds.

I know that this is a quite common problem on the forum, but I haven't found anything yet that could solve this.

Thank you for your help,
EliI

---

### Post by elii on 2007-02-24
... bump ...

Sorry, but this is quite a common issue and I have yet to see a solution.

Any help is appreciated...

---

### Post by elii on 2007-02-24
It would appear I managed to fix this, so here's what I did:

The thing that most probably solved the problem was using Static IP and DNS configuration (via System->Administration->Networking), supplying both the IP address of the eth and the DNS server. I got this addresses by doing ifconfig (and ipconfig /all on my WinXP boot) after connecting with dynamic configuration.

Also, I did several more things that I found around the forums:
1. Disabling IPv6 on Firefox. Go to about:config and add or change the binary ipv6 value to true. This is supposed to filter  IPv6 traffic from Firefox.
2. Disabling IPv6 entirely on the Ubuntu. By adding blacklist-ipv6 to /etc/modprobe.d/ with "blacklist ipv6". You can see if this worked by "lsmod | grep ipv6". It shouldn't return anything (after a reboot/X restart), though mine still did, so I might have done something wrong.
3. Setting the DNS addresses manually. I don't know if this is necessary if you already to this through the Networking GUI, but still. In /etc/resolv.conf add "nameserver x.x.x.x" for every DNS address you have. Also in /etc/dhcp3/dhclient.conf set the "prepend domain-name-servers" with your DNS address ("prepend domain-name-servers a.a.a.a,b.b.b.b;"). Finally remove "domain-name-servers" from the "request" line of the same file.
4. Set a DHCP lease time. n /etc/dhcp3/dhclient.conf set "send dhcp-lease-time" to some number. I tried 3600, but I guess you can play with it and see if it helps.

From all the solutions I found, there might be several causes to the probelm - old or cheap DSL routers/modems that don't support IPv6 (thus disabling it should help). DSL routers/modems that are very Windows specific, having problems with Linux implementation (Microsof's implementation is know to be non-standard, most notably in the protocol stack and in the Internet Explorer) might not work well with a dynamic configuration. DNS servers that don't talk very well through the DSL router/modem (thus supplying their address yourself will help).
. 
As always, make sure you backup any files you change.

Hope this helps anyone.

EliI

---

