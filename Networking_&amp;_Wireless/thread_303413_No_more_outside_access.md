---
title: "No more outside access"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by randomi on 2006-11-20
So I successfully installed a completely customized LAMP install (I think, it's my first time... don't know if it all works or not). Well once everything was all set up I tried to install a package, and none of the repositories could be reached. As of right now I've just spent 2 hours trying to figure out what is going on. I have it set up with dhcp but on my router I have an ip reserved for my server. Should be using the isp's dns servers for anything outside of the domain that I have for the server. Any ideas on what I might have done to get myself into a corner like this?

Current Install:

Dapper Server kernel
Apache
MySQL 4
PHP 4
BIND
postfix
Courier IMAP/POP
ProFTPD

It's probably something simple that I'm overlooking or something dumb I did while I was configuring everything, but any help getting it working again would be great.

---

### Post by dannyboy79 on 2006-11-21
are your dns servers defined in your /etc/network/interfaces file? If you have a router than I know that your isp's dns server's are defined there and you probably have your router defined as the default gateway so you would think that name resolution would work by going to your router and then hitting your isp's dns servers well I have added my isp's dns servers to my interfaces file and that seemed to have solved the problem. mine looks like the following:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 24.94.163.33

also, if you do a cat /etc/resolv.conf, is your dns server listed??

1 last thing to check, i always add dns servers ip address within the gui under networking but if you're on a lamp server and you don't have a gui, you could look in 1 last place. i looked within /etc/resolvconf/resolv.conf.d/ and there is a file called original. mine looks like the following.


domain LINUX
nameserver 24.94.163.33
search LINUX
nameserver 24.94.163.34
nameserver 192.168.0.1

good luck

oh yeah, have you looked at your log files???? /var/log/syslog or /var/log/dmesg or /var/log/messages, all these always tell ya things!

---

