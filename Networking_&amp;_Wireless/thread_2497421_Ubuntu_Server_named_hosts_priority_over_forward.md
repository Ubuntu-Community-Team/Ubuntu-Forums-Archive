---
title: "Ubuntu Server named hosts priority over forward"
date: 2024-05-03
forum: Networking &amp; Wireless
---

### Post by lisanels47 on 2024-05-03
I have a ubuntu server working great, but would like to adjust how the named service responds to DNS requests.

For example; I put 127.0.0.1 in the hosts file on the server for go.microsoft.com.  
nsswitch is set to:   "hosts:          files  dns"

On the server if I issue 'host go.microsoft.com' it responds with 127.0.0.1.  Great.
On a Ubuntu 24.04 client with the server set as the DNS nameserver, the server evidently forwards that request and the normal ip address results.

Is there a way for named to be set so it does not forward a request if an entry in the hosts file matches?  Then only return the ip address that is in the hosts file?

---

### Post by TheFu on 2024-05-04
Uh ... you can't just do that. That's asking for problems.
127.0.0.1 go.microsoft.com

You can use any 127.x.x.x/8 ip that you want, just be certain it isn't already being used for some other need.  127.x.x.x/8 is loopback/localhost. That's 
```
$ ipcalc 127.0.0.1/8
Address:   127.0.0.1            01111111. 00000000.00000000.00000001
Netmask:   255.0.0.0 = 8        11111111. 00000000.00000000.00000000
Wildcard:  0.255.255.255        00000000. 11111111.11111111.11111111
=>
Network:   127.0.0.0/8          01111111. 00000000.00000000.00000000
HostMin:   127.0.0.1            01111111. 00000000.00000000.00000001
HostMax:   127.255.255.254      01111111. 11111111.11111111.11111110
Broadcast: 127.255.255.255      01111111. 11111111.11111111.11111111
Hosts/Net: 16777214              Class A, Loopback
```
about 16M possible choices.  That may help you understand the 127.0.0.53 in the /etc/resolv.conf being used as a DNS caching server.

What exactly, do you mean by "Ubuntu 24.04 client"?  Different programs handle DNS differently, though they shouldn't.  Web browsers, for about the last 10 yrs, have decided they knew more about DNS than the local admin did and a few of those browsers ignore the OS DNS settings and do their own thing.  Google-Chrome and Firefox have both done this in the claim of "security".  Alas, for people who never want to run any internal servers, that might be true.  But for people trying to run stuff on their own LAN, those choices break things.

A browser engine might also run foul with these choices, so Electron-applications (glorified web browsers wrapped in a GUI) can also behave that way.

Firefox has a way to disable their DNS override, but not a way to enable local files to be used.  Android is worse.  Basically, you'll need to run a local DNS for Android browsers to use.  Of course, this may change at any time and I haven't looked into these issues for a few years.  I decided that having a local DNS would solve the issues and I'd be done.  It has worked that way for me.  I use a set of pihole systems running in lxc containers on 2 different physical systems.  DNS needs a primary and a backup or when the only DNS is down for patching/maintenance, your entire network will feel "down."  The pihole systems running in containers are very light.  Or you could use an old r-piv2 and run it there.  DNS isn't a huge RAM or CPU hog.

---

