---
title: "Cannot resolve hostnames on local network (e.g. Mothership.local) on Lubuntu 13.10"
date: 2013-12-30
forum: Networking &amp; Wireless
---

### Post by krcrouse on 2013-12-30
Hi all,

i know this is a longstanding type of topic, but my issues are somewhat different.  I recently updated all of my machines to Lubuntu 13.10 (and I install gnome-shell on one, but still from a base of lubuntu).  All machines on my local network are Ubuntu, Android, and my partner has a Mac.  

With the new installs, I can't access my machines by hostname (e.g. Mothership.local, Transformation.local).  I can't use the old /etc/host.conf solution that specifies IP address for hosts because IP addresses will regularly change because I use a Belkin router that doesn't allow reserving ip addresses in DHCP.  That's also the main reason why I want to be able to access them by hostname, otherwise I'd just ssh/scp using ip addresses.

Thanks for the help.  Of course, I've verified I can get into the machines using ip addresses.  I've copied some typical config files below:

 cat /etc/hosts:
127.0.0.1 localhost
127.0.1.1 Mothership  # hostname of the machine.  Verified that this is also returned by hostname

 cat /etc/host.conf
order hosts, bind
multi on

 cat /etc/resolv.conf
nameserver 127.0.1.1
search Dialog # Dialog is the domain of the router

---

### Post by Iowan on 2013-12-30
DHCP/DNS is the primary reason I have a separate machine running Dnsmasq - so I can ping/SSH by hostname. My Tomato router is supposed to use Dnsmasq, but i apparently don't have it set up right - it doesn't remember hostnames.

---

### Post by steeldriver on 2013-12-30
The .local resolution should be provided by avahi - have you checked that the avahi-daemon service is running on all the machines?

```
service avahi-daemon status
```

---

### Post by krcrouse on 2013-12-30
Thanks steeldriver, that sent me on the right path.  avahi-daemon was installed and running in my lubuntus already (thought your command, *service avahi-daemon status*, didn't return anything).  

But after installing the **libnss-mdns** package, and editing **/etc/nsswitch.conf** to read:

[FONT=courier new]  hosts: files mdns4_minimal [NOTFOUND=return] dns[/FONT]

Everything works.  Originally, that line just said *hosts: files dns*

Thanks folks!

---

