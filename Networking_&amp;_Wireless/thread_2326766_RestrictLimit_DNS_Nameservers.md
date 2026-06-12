---
title: "Restrict|Limit DNS Nameservers?"
date: 2016-06-04
forum: Networking &amp; Wireless
---

### Post by maxwellcom on 2016-06-04
Hello,

I'm running local DNS (BIND9 on primary and secondary Ubuntu servers).  On my Ubuntu desktop, however, I've noticed that while it usually seems to be resolving addresses properly with the local DNS servers, it actually lists *four* DNS nameservers.  The first two are my local DNS (RPi) machines, but third and fourth are my local ISP's nameservers:

```
nmcli dev show | grep DNS
IP4.DNS[1]:                             192.168.0.2
IP4.DNS[2]:                             192.168.0.3
IP4.DNS[3]:                             75.75.75.75
IP4.DNS[4]:                             75.75.76.76
```

The /etc/network/interfaces on the local DNS looks like this:

```
# primary network interface
allow-hotplug eth0
iface eth0 inet static
        address 192.168.0.2
        netmask 255.255.255.0
        gateway 192.168.0.1
        broadcast 192.168.0.255
dns-search home.lan
dns-domain home.lan
dns-nameservers 192.168.0.2 192.168.0.3 192.168.0.2 192.168.0.3
```

I'd like to restrict all connected members of the network to only the two local DNS nameservers.  Any advice or suggestions is greatly appreciated!

---

### Post by SeijiSensei on 2016-06-04
Just an aside, but your machine will never touch those nameservers as long as 192.168.0.2 or 192.168.0.3 are available.  DNS servers in [resolv.conf]("http://man7.org/linux/man-pages/man5/resolv.conf.5.html") are not consulted in a "round-robin" fashion unless you specifically request it to with the "rotate" option.

I'm assuming your internal name servers can resolve external addresses.  Just to make sure, run the command "host [www.google.com](www.google.com) 192.168.0.2" from a command prompt. You should get back a list of addresses for that name.

I usually specify name servers and other things like search domains in /etc/resolvconf/resolv.conf.d/head.  See "man resolvconf" for details.  As an extreme measure, you can create /etc/resolv.conf manually and mark it "immutable" with "sudo chattr +i /etc/resolv.conf".  That will block any programs like resolvconf from changing the contents of the file.

---

