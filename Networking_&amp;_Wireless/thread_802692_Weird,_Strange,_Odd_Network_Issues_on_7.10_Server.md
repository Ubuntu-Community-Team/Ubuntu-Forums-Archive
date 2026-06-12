---
title: "Weird, Strange, Odd Network Issues on 7.10 Server"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by mootpoint on 2008-05-21
Whoever fixes this gets a prize. :-)

I'm trying to (finally) replace my antique P3 home server with a newer box. So over the weekend I upgraded it from Ubuntu 7.04 to 7.10 (no problems, and I don't think this caused the problem ... see below), finished up my email server config (postfix with all the usual addons), all that happy stuff. Except I am seeing very strange problems:

1) When I try to send email from the box, postfix queues up the mail as a DNS failure. However, tcpdump shows no DNS request ever left the network interface. These outbound mail DNS lookups always fail. However, dig yahoo.com mx (or pick your domain name) works fine from bash.

2) When inbound mail connections come in, some work and some don't. Test messages from yahoo.com work. Messages from msn.com do not. Overall, about 50% of incoming mail from the world works, about 50% does not. It's all or nothing for each sending server; the ones that work always work, the ones that don't never do.

3) tcpdump shows the usual packet traces for the inbound mail that works. For the ones that fail, a TCP syn comes in from the source, and the box simply does not answer.

4) Before the Ubuntu version upgrade, I would sometimes run a torrent on this box (Linux mint .iso's). It would run for several hours, up to a day or so, and the NIC would simply stop working. I'm assuming that behavior and what I'm current wrestling with probably have the same cause.

Additional configuration info:

a) I have the MTU on eth0 set to 1420 bytes, to make sure my PPPOE DSL line doesn't fragment packets. The old server has the same MTU, and it works great.

b) File transfers, both on the local network and over the internet, work great. Perfect. No problems. 

Here's the snippet from lspci identifying the NIC:

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)

dmesg has nothing bad or unusual in it. 

Kernel info:  

[    0.000000] Linux version 2.6.22-14-server (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 08:27:05 UTC 2008 (Ubuntu 2.6.22-14.52-server)

Anyone have any idea at all? 

doc

---

### Post by dmizer on 2008-05-22
not too sure what to tell you, but there are a few things to try:

kill ipv6 unless you need it: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?)

use open dns servers:
[https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

is this a problem specific to email only?  (apt, and browsing works fine)
are you using wins for local name resolution?
firewall? (firestarter)

---

### Post by mootpoint on 2008-05-22
Well, apt-get --purge remove postfix and a reinstall fixed things. It wasn't configuration, since I backed up /etc/postfix and restored all the same config files afterwards. 

Weird.

m00t

---

