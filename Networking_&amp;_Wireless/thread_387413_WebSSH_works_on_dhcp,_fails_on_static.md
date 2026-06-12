---
title: "Web/SSH works on dhcp, fails on static"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by bakert on 2007-03-18
I have set up a webserver (no X) behind a D-Link router.

Initially I installed it with DHCP and it could resolve names, get to my other ssh server and web sites fine.

When I edited /etc/network/interfaces to set up a static IP this stopped working.

With the static IP I can still "ping google.com", resolve and get replies but ssh and w3m now fail to resolve the name.  If I ping it just before I try it the name is resolved but it doesn't get any further than the SYN_SENT state and eventually times out.

My best guess is that using DHCP causes something to be set up on the router that static IP does not??  But this is the end of my knowledge.  I'd really appreciate it if someone could give me a pointer.  Thanks!

Oh, my /etc/network/interfaces now looks like this:

auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.0.255
gateway 192.168.1.1

---

### Post by chili555 on 2007-03-18
Should broadcast be 192.168.**1**.255? Or, was that a typo?

---

### Post by bukwirm on 2007-03-18
If that doesn't work, try disabling IPv6, and setting your ISP's DNS servers explicitly (ie. not "Detect Automatically, actually enter their IP addresses) in your router's config.

---

### Post by lloyd_b on 2007-03-18
First, a comment:  The "network" line you have in your interfaces file is redundant - given the IP address and netmask, Linux will automatically add the appropriate route for that network.

Second - if the previous suggestions don't help, could you post the output of the "route -n" command? 

Lloyd B.

---

### Post by bakert on 2007-03-24
Thanks for your help guys.  Been at work all week but now I'm going to get this working, I swear!

I disabled ipv6 and added my ISP's nameserver in place of the router IP in the server's /etc/resolv.conf

In this state name resolution woks fine.  That is ssh -v successfully resolves the name of the server I want to get to.  Also "host google.com" no longer reports anything about malformed packets.  Great.

Buuuuuuut, with a static IP I still can't actually ssh anywhere or visit anything in a web browser.

On DHCP I can (although of course DHCP overwrites my /etc/resolv.conf giving me name resolution issues, plus I really want this machine on a static IP).

While set up with the static IP I get:

[PHP]bakert@zaphod:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
[/PHP]
Any ideas?

---

### Post by bakert on 2007-03-24
Using tcpdump I can see that some kind of communication is going on between my server and the machine I am trying to ssh to.

This sequence seems to be repeated every few seconds for a very long time.  This is from the end I am ssh-ing /to/.  I changed the ip and the host name for "security".

[PHP]09:29:48.343890 IP mcs2.example.com.ssh > 82-99-244-44.dsl.in-addr.zen.co.uk.41247: P 21232:21440(208) ack 369 win 3228 <nop,nop,timestamp 68517562 12116605>
09:29:48.344001 IP mcs2.example.com.ssh > 82-99-244-44.dsl.in-addr.zen.co.uk.41247: P 21440:21648(208) ack 369 win 3228 <nop,nop,timestamp 68517562 12116605>
09:29:48.344084 IP mcs2.example.com.ssh > 82-99-244-44.dsl.in-addr.zen.co.uk.41247: P 21648:21856(208) ack 369 win 3228 <nop,nop,timestamp 68517562 12116605>
09:29:48.387302 IP 82-99-244-44.dsl.in-addr.zen.co.uk.41247 > mcs2.example.com.ssh: . ack 21440 win 15791 <nop,nop,timestamp 12121147 68517562>
09:29:48.387352 IP mcs2.example.com.ssh > 82-99-244-44.dsl.in-addr.zen.co.uk.41247: P 21856:22832(976) ack 369 win 3228 <nop,nop,timestamp 68517567 12121147>
09:29:48.390818 IP 82-99-244-44.dsl.in-addr.zen.co.uk.41247 > mcs2.example.com.ssh: . ack 21648 win 15791 <nop,nop,timestamp 12121147 68517562>
09:29:48.390859 IP 82-99-244-44.dsl.in-addr.zen.co.uk.41247 > mcs2.example.com.ssh: . ack 21856 win 15791 <nop,nop,timestamp 12121147 68517562>
09:29:48.438637 IP 82-99-244-44.dsl.in-addr.zen.co.uk.41247 > mcs2.example.com.ssh: . ack 22832 win 15791 <nop,nop,timestamp 12121158 68517567>[/PHP]

So my badly informed guess is that everything is going fine up until the point where the remote machine responds.  And my router is somehow set to drop the responses when I have a static IP but not when I have a DHCP address.  Unfortunately my knowledge of networking is being stretched to its limit here and I'm not sure where to go next.

---

### Post by bakert on 2007-03-24
Another interesting featurette.  Even though I have a static IP, my /etc/resolv.conf is still getting periodically overwritten with "nameserver 192.168.1.1".  So perhaps I have some service running that can't get it through it's head I'm not running dhcp???

---

### Post by bakert on 2007-03-24
Hmm.

I got it working but I'm unimpressed with my setup.  Perhaps someone can offer some pointers?

What works is this:

- setup /etc/network/interfaces with a static IP that is IN the dhcp range, not outside it as I was doing.
- edit /etc/dhcp3/dhcp3.conf to have a "supersede" line that sets /etc/resolv.conf to my ISP's nameservers.

So I'm /kind of/ running with a static IP and kind of not.  I wonder if the DHCP server will ever try and give out the same address causing great problems?

Hmm.  Oh well, at least it works and I can get on with my life!

If anyone understands this better than me I'd love to know what you think is going on and what might be a more sensible approach.  Thanks!

---

