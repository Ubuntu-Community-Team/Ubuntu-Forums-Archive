---
title: "Server 14.04 LTS - Removed Network-Manager Now No Access To Local Web Server Domain"
date: 2015-01-17
forum: Networking &amp; Wireless
---

### Post by daryl6 on 2015-01-17
Hi everyone. I need help please. I am self-educating myself on Ubuntu  Server & I played around with a Virtual Box VM by removing &  purging network-manager & all related packages to network-manager,  including network-manager-openconnect. I then reinstalled it but I don't  know how to configure it to work like it did before. Nothing I do will  make it work. I can access ssh/putty by I.P. Address only, But NOT host  name / domain name. I can't access the Nginx Web Server using the host  name from my Windows Computer's Browser either, BUT I Can Access It By  Using I.P. Address, same as SSH / Putty access. If anyone can help me  know what to do to reconfigure everything back to the way it was before I  ever uninstalled & purged the packages & settings, I would  sincerely appreciate it. Thanks!

---

### Post by TheFu on 2015-01-18
Don't know anything about network-manager - I don't use it.
As to finding machines on your network - did you modify the /etc/hosts file on all the machines to have the IP address for all the machines you want that machine to locate?  That is the way IP-to-name resolution works if you don't run a DNS server or have a domainname purchased for each machine on the internet.

---

### Post by steeldriver on 2015-01-18
I didn't think the server editions used network-manager by default anyhow?

Can you clarify what you mean by "access by hostname / domain name"? if you are referring to mDNS addressing (like mypc1.local, mypc2.local) that would be handled by the avahi service, I think.

---

### Post by TheFu on 2015-01-18
On my network, with about 25 Ubuntu servers 10.04, 12.04 and 14.04, the only way hosts can find each other are through /etc/hosts management.  The router DNS is just a cache, dosn't know anything internally.    Avahi is running and perhaps it knows how to find itself because of this, but that doesn't help it find any other systems.

My curiosity found this: [http://askubuntu.com/questions/2631/access-server-by-host-name](http://askubuntu.com/questions/2631/access-server-by-host-name) - says that appending .local to find other hosts on the subnet should work.  From a host running avahi, I tried to find another machine, also running avahi, but it failed.
```
$ ping c720.local
ping: unknown host c720.local

```
Ping without the .local works - because all my systems have a shared /etc/hosts file that knows all the systems on the subnet. I use static DHCP leases for portable devices and static IPs for all the others.  Ansible is used to manage the hosts file and push any updates to any systems needing updates.  Of course, with a recent home router, many will support DHCP leases and DNS for internal use: [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) explains.  This does work, but I prefer to manage /etc/hosts files .. since when I'm on travel, my internal DNS isn't available.

---

