---
title: "OpenVPN / TUN / Dapper - Error 19"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by nickmilleruk on 2008-04-14
Hi,

I am quite new to OpenVPN and VPN in general. I have two servers located at different locations and need to create a VPN between them.

The VPN server is running Dapper (Ubuntu 6.06.1 LTS) and I am using OpenVPN 2.0.6 i486-pc-linux-gnu

I have created a really basic configuration file:

dev tun
ifconfig 10.8.0.1 10.8.0.2
secret /root/static.key

When I run the run openvpn (openvpn --config /etc/openvpn/openvpn.conf I get the following:

Mon Apr 14 23:43:18 2008 OpenVPN 2.0.6 i486-pc-linux-gnu [SSL] [LZO] [EPOLL] built on Apr 10 2006
Mon Apr 14 23:43:18 2008 IMPORTANT: OpenVPN's default port number is now 1194, based on an official port number assignment by IANA.  OpenVPN 2.0-beta16 and earlier used 5000 as the default port.
Mon Apr 14 23:43:18 2008 Note: Cannot open TUN/TAP dev /dev/net/tun: No such device (errno=19)
Mon Apr 14 23:43:18 2008 Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Mon Apr 14 23:43:18 2008 Cannot allocate TUN/TAP dev dynamically
Mon Apr 14 23:43:18 2008 Exiting


I wanted to check I have /dev/net/tun and I see:

crw-r--r-- 1 root root 10, 200 Dec 14 10:41 tun

I do modprobe tun and I get:
modprobe: Can't open dependencies file /lib/modules/2.6.9-023stab044.4-enterprise/modules.dep (No such file or directory)

If I do lsmod | grep tun I get:
lsmod: QM_MODULES: Function not implemented

This is really frustrating me - either my lack of knowledge prevents me from understanding the articles I find in Google or everyone has a slightly different problem making it hard to figure out whats going on :(

Any help is greatly appreciated

Nick

:KS

---

