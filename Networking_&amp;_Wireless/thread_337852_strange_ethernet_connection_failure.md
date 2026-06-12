---
title: "strange ethernet connection failure"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by inportb on 2007-01-13
I'm not sure where to ask about this, because most forum-users who have connectivity problems seem to have no connectivity at all. I am able to connect, but the connection always fails after a while. Obviously, I am online now, and able to post this message.

I am running (k)Ubuntu 6.10 (Edgy Eft) on a Toshiba Satellite L25-S119 laptop. I use the latest stable KDE, and the KNetDockApp applet to visually monitor traffic. I am on a wired (ethernet) network.

When the computer boots up and I login to a new KDE session, the network is fine. I type "ip link" and get the following:


$ ip link
1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: wifi0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 199
    link/ieee802.11 00:11:f5:8d:ca:ea brd ff:ff:ff:ff:ff:ff
3: ath0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc noqueue
    link/ether 00:11:f5:8d:ca:ea brd ff:ff:ff:ff:ff:ff
4: eth0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:c0:9f:dd:e1:0c brd ff:ff:ff:ff:ff:ff
5: sit0: <NOARP> mtu 1480 qdisc noop
    link/sit 0.0.0.0 brd 0.0.0.0


eth0 is the ethernet adapter of interest.

I can browse web pages in Firefox and Konqueror... No problems there. To make sure everything is okay, I disable and enable eth0:


$ sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 4524
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:c0:9f:dd:e1:0c
Sending on   LPF/eth0/00:c0:9f:dd:e1:0c
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 128.59.62.25 port 67


Okay, KNetDockApp complains that it cannot communicate with eth0, which is normal. I enable it again:


$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:c0:9f:dd:e1:0c
Sending on   LPF/eth0/00:c0:9f:dd:e1:0c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 160.39.144.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 160.39.144.1
bound to 160.39.147.57 -- renewal in 1597 seconds.


It looks like the DHCP client is okay. Connectivity is restored, and I am able to browse web pages, SSH, FTP, and so on.

After a while, I notice that web pages stop loading. Firefox does not display the familiar connection-timed-out screen, so something is going on here. I check KNetDockApp and see that there is zero traffic on eth0, and lo (loopback) seems to have some activity (it did not, before). So I try to repair the connection by disabling and enabling eth0:


$ sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 4679
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:c0:9f:dd:e1:0c
Sending on   LPF/eth0/00:c0:9f:dd:e1:0c
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 128.59.62.25 port 67


Okay, eth0 is down now. Firefox says _now_ that the connection is timed out. KNetDockApp complains as usual. I bring eth0 back up:


$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:c0:9f:dd:e1:0c
Sending on   LPF/eth0/00:c0:9f:dd:e1:0c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Now, it _appears_ that the DHCP server is not responding. If I want to get a connection, I have to reboot the whole computer.

Does anyone see anything wrong? What other tests can I run?

Thanks so much!

---

### Post by scrooge_74 on 2007-01-13
type sudo dhclient eth0

also get DNS server ip and put them in your resolv.conf so you dont have to depend on the router.

You can also try rebooting the router

---

### Post by raspi on 2007-01-13
If problem is DHCP:

1. Try only get new IP from DHCP with **dhclient eth0** and don't try to bring down & up eth0 every time.

2. Try different DHCP client. There's dhclient, dhcpcd and few others (search DHCP with synaptic or aptitude)

3. Paste few last TCP/IP packets to this forum. Install netwox, tcpdump, ipgrab, wireshark (ethereal).

Also your firewall may block DHCP packets.

---

### Post by inportb on 2007-01-13
Thank you for your responses! I will try dhclient (in my process listing, there is a dhclient3, should I use that instead?) when the network dies again. I'm at the [Columbia] university right now, so I can't do much about the router configuration xD.

I'm not sure about the firewall. I used to run WinXP on this machine, on the same network, and this never happened. Unless it's a firewall installed on this machine... and I don't recall installing a firewall.

The problem seems to be related to FTP. I've been doing some web development lately, and have been FTP'ing and browsing quite a bit. It usually happens right after I upload a file, just when I'm about to switch to the web browser. I reduced FTP usage, and problem occurrence also decreased. I made the machine hibernate when the problem occurred. When I revived the machine, networking works... until it dies again. I suspect that it may not be an issue with software configuration. Hibernating and reviving may have fixed the problem by forcing eth0 to restart completely. Hmm...

Anyhow, I'm going to make eth0 die again deliberately (by FTP'ing more) and try dhclient. And i'll tweak resolv.conf and see what happens. Thanks again for your help!

###EDIT###
Hmm... Now that I'm trying to reproduce the error, it doesn't want to occur. Maybe it's a different cause. Anyway, I'll keep going until it dies again, and if it does, I'll let you know how it goes.

---

### Post by inportb on 2007-01-20
Okay. I get the feeling that this happens when I open a page in Firefox and the server does not respond. For example, Wordnet <http://wordnet.princeton.edu/> was not working today, and when I navigate to the URL, I [expect to] get a connection-timed-out message in Firefox. Sometimes I never get that message. Instead, I see that my network connection is dead. Firefox is obviously expecting data because it does not say that the connection has timed out, when it should have timed out already.

I tried **dhclient eth0**, but I get the same DHCP error message. It might not be a problem with DHCP. Is it possible that the connection to the unresponding server is tying everything else up? If so, how can the rogue connection be killed/prevented?

---

### Post by inportb on 2007-04-21
Three months later, I discover the cause of my troubles -- CPU frequency scaling.

This only happens when I add p4_clockmod and cpufreq_* to /etc/modules. If I remove the modules from the list and reboot, the network stays working. It's not enough to simply unload the modules.

* = userspace, ondemand, conservative, performance, stat
My laptop runs on a Celeron M CPU and has Kubuntu Feisty Fawn installed.

Is it possible to have both CPU scaling and networking?

Thanks!

---

