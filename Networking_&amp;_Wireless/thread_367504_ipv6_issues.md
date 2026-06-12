---
title: "ipv6 issues"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by ubunutgoz on 2007-02-22
Hi Ubuntu people, am an Ubunte Newbie, so please bear with me...

In short, my problem is installing new software.  I thought I had got somewhere with ipv6, but still get the messages (see below).  I did get the updates, and installed in the last hour or so.

What I want to do is install stuff like VLC, SKYPE, REALPLAYER etc...

Here's a brief history Edgy-Eft 6.10

1 - Downloaded DVD and installed in non-graphical mode - all ok except FIREFOX wouldn't work.
2 - changed some setting in FIREFOX including turning ipv6 off, and also adjusting some network.http.. setting - ALL WORKED
3 - tried to install VLC, but couldn't update the application register
4 - looked around and learned that i needed to diasble ipv6 in /etc/modprobe.d/aliases using the command **alias net-pf-10 off ipv6**
5 - then lo and behold, the system recognised i needed security updates, which of course i did.
6 - now FIREFOX didn't work, checked settings were still the same (they were).  So in /etc/modporbe.d/aliases I turned ipv6 back on, FIREFOX worked! 
7 - But still can't down load new software.

And this is where I am now, not able to add new software, and wondering if the alias **net-pf-10 off ipv6 ** needs to be changed everytime I want to check for security update.

I REALLY REALLY want to get away from Uncle Bill, but this is getting to be a chore.  I simply want to use my machine!
[B]
HARDWARE[/B]
IBM Thinkpad r50e
256k RAM (I will be upgrading!)
40G disk
Intel IPW2200 interner card
D-Link 604 wireless router 

Just a thought, would this all go away if I plugged cable between router and computer?

So, Please, if anyone can point me in the right direction, please help.
Many thanks
Alan

[http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_GB.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_GB.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_GB.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_GB.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_GB.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_GB.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_GB.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_GB.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_GB.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_GB.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_GB.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_GB.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_GB.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_GB.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_GB.bz2:](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_GB.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_GB.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_GB.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_GB.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_GB.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_GB.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/i18n/Translation-en_GB.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_GB.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_GB.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://packages.freecontrib.org/ubuntu/plf/dists/edgy-eft/Release.gpg:](http://packages.freecontrib.org/ubuntu/plf/dists/edgy-eft/Release.gpg:) Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
[http://packages.freecontrib.org/ubuntu/plf/dists/edgy-eft/free/i18n/Translation-en_GB.bz2:](http://packages.freecontrib.org/ubuntu/plf/dists/edgy-eft/free/i18n/Translation-en_GB.bz2:) Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
[http://packages.freecontrib.org/ubuntu/plf/dists/edgy-eft/non-free/i18n/Translation-en_GB.bz2:](http://packages.freecontrib.org/ubuntu/plf/dists/edgy-eft/non-free/i18n/Translation-en_GB.bz2:) Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
[http://medibuntu.sos-sts.com/repo/dists/edgy-eft/Release.gpg:](http://medibuntu.sos-sts.com/repo/dists/edgy-eft/Release.gpg:) Could not connect to medibuntu.sos-sts.com:80 (1.0.0.0), connection timed out
[http://medibuntu.sos-sts.com/repo/dists/edgy-eft/free/i18n/Translation-en_GB.bz2:](http://medibuntu.sos-sts.com/repo/dists/edgy-eft/free/i18n/Translation-en_GB.bz2:) Could not connect to medibuntu.sos-sts.com:80 (1.0.0.0), connection timed out

---

### Post by Dumdideldum on 2007-02-22
seems like there is an issue with dns - not sure though but (1.0.0.0) is not the proper IP for the apt-server.

what happens if you do a:
ping archive.ubuntu.com ?

furthermore, post your 
/etc/nsswitch.conf
/etc/resolv.conf
/etc/hosts

---

### Post by ubunutgoz on 2007-02-22
Thanks for reply... 

Here's the ping

64 bytes from archive.ubuntu.com (91.189.89.182): icmp_seq=20 ttl=54 time=107 ms
64 bytes from archive.ubuntu.com (91.189.89.182): icmp_seq=21 ttl=53 time=218 ms
64 bytes from archive.ubuntu.com (91.189.89.182): icmp_seq=22 ttl=53 time=125 ms
64 bytes from archive.ubuntu.com (91.189.89.182): icmp_seq=23 ttl=53 time=98.7 ms
64 bytes from archive.ubuntu.com (91.189.89.182): icmp_seq=24 ttl=53 time=121 ms
64 bytes from archive.ubuntu.com (91.189.89.182): icmp_seq=25 ttl=53 time=226 ms
64 bytes from archive.ubuntu.com (91.189.89.182): icmp_seq=26 ttl=53 time=111 ms
64 bytes from archive.ubuntu.com (91.189.89.182): icmp_seq=27 ttl=53 time=104 ms
64 bytes from archive.ubuntu.com (91.189.89.182): icmp_seq=28 ttl=54 time=140 ms
64 bytes from archive.ubuntu.com (91.189.89.182): icmp_seq=29 ttl=53 time=110 ms
64 bytes from archive.ubuntu.com (91.189.89.182): icmp_seq=30 ttl=54 time=120 ms

and here's the file listings..

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
_______________________________________________
/etc/resolv.conf

nameserver 192.168.1.1
______________________________________________
/etc/hosts

127.0.0.1	localhost
127.0.1.1	ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts



HOPE THAT MEANS SOMETHING TO YOU!!! :-)
thanks
alan

PSs 
- I have #'d out all ipv6 reference in the kernel config files
- I have tried using openDNS DNSs
- I have trid to turn ipv6 off!

---

