---
title: "Local network fine but no internet access"
date: 2015-02-23
forum: Networking &amp; Wireless
---

### Post by iurisilveira on 2015-02-23
Hi, I am experiencing an interesting situation.

One of my Ubuntu boxes (14.04 LTS) is not connecting to the internet, although I can view and be viewed by other hosts and by the router in my network.

All other systems (variety of Ubuntu 12.04, 14.04, Windows Server, Windows XP, Vista, 8, Android, Apple) in the same network are working fine, connecting to the internet and can ping and be pinged. I have Comcast/XFynity and I am using the default DHCP, only changed the range to start on .100 so I can configure a couple servers and printers with low ip addresses, below .100. And obviously my ip is not blocked or filtered in the router. Also there are no IP conflicts.

I have one printer shared in my 14.04 box and other systems can print to this printer. I have a couple shared folders and they can be accessed in the network. It can also be viewed through VNC. So I don't see a problem with local network.
But if I open a browser (Chrome or Firefox) the page times out after "resolving hosts" message is shown for a minute at the bottom (Chrome) or spins on connecting... (FF).

This is some information from my box:
Compaq AMD Athlon 7550 Dual-Core x2 / 4GiB RAM
Graphics: Gallium 0.4 on AMD RV610
Ubuntu 14.04 LTS 32 bit

Network info from ifconfig:[INDENT]eth0      Link encap:Ethernet  HWaddr 00:26:18:0c:ed:3e  [/INDENT]
[INDENT]          inet addr:10.0.0.114  Bcast:10.0.0.255  Mask:255.255.255.0[/INDENT]
[INDENT]          inet6 addr: fe80::226:18ff:fe0c:ed3e/64 Scope:Link[/INDENT]
[INDENT]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/INDENT]
[INDENT]          RX packets:4170 errors:0 dropped:16 overruns:0 frame:0[/INDENT]
[INDENT]          TX packets:2038 errors:0 dropped:0 overruns:0 carrier:0[/INDENT]
[INDENT]          collisions:0 txqueuelen:1000 [/INDENT]
[INDENT]          RX bytes:442976 (442.9 KB)  TX bytes:311864 (311.8 KB)[/INDENT]
[INDENT]
[/INDENT]
[INDENT]lo        Link encap:Local Loopback  [/INDENT]
[INDENT]          inet addr:127.0.0.1  Mask:255.0.0.0[/INDENT]
[INDENT]          inet6 addr: ::1/128 Scope:Host[/INDENT]
[INDENT]          UP LOOPBACK RUNNING  MTU:65536  Metric:1[/INDENT]
[INDENT]          RX packets:191 errors:0 dropped:0 overruns:0 frame:0[/INDENT]
[INDENT]          TX packets:191 errors:0 dropped:0 overruns:0 carrier:0[/INDENT]
[INDENT]          collisions:0 txqueuelen:0 [/INDENT]
[INDENT]          RX bytes:28490 (28.4 KB)  TX bytes:28490 (28.4 KB)[/INDENT]


My Hosts file:[INDENT]# BEGIN hosts added by Network Connect[/INDENT]
[INDENT]47.213.74.149  vpn.dltcomm.com[/INDENT]
[INDENT]# END hosts added by Network Connect[/INDENT]
[INDENT]127.0.0.1    localhost[/INDENT]
[INDENT]127.0.1.1    Compaq[/INDENT]
[INDENT]
[/INDENT]
[INDENT]# The following lines are desirable for IPv6 capable hosts[/INDENT]
[INDENT]::1     ip6-localhost ip6-loopback[/INDENT]
[INDENT]fe00::0 ip6-localnet[/INDENT]
[INDENT]ff00::0 ip6-mcastprefix[/INDENT]
[INDENT]ff02::1 ip6-allnodes[/INDENT]
[INDENT]ff02::2 ip6-allrouters

[/INDENT]

(I just scrambled some information for security reasons where the VPN information is.)

I was curious enough to try the IP address instead of website addresses and it works. For instance "google.com" traces to 64.233.176.105 and if I enter this address on browser the page loads. Same for "cnn.com" 157.166.226.26, although many parts of these pages fail since they refer to addresses and not IPs.

So I guess I have a DNS problem on my ubuntu box. I am not an expert in ubuntu network configuration, so please guide me on how to further troubleshoot this issue. Any assistance is welcome. Thank you!

---

### Post by TheFu on 2015-02-24
> **iurisilveira said:**
> 
So I guess I have a DNS problem on my ubuntu box. I am not an expert in ubuntu network configuration, so please guide me on how to further troubleshoot this issue. Any assistance is welcome. Thank you!

I agree that DNS is likely the issue.

routes and dns settings?

---

### Post by iurisilveira on 2015-02-24
Where exactly I can get that? I only suspect they are in the /etc folder.

---

### Post by TheFu on 2015-02-25
> **iurisilveira said:**
> Where exactly I can get that? I only suspect they are in the /etc folder.

[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) has basic network troubleshooting tips. I suspect you've already solved this.

Sadly, the [https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic) version is 2+ yrs out of date for DNS stuff. I couldn't figure out how to edit it with corrections. Sorry. No edit button on the wiki.

The Server Networking documents are correct for 14.04. Didn't look at any others.

---

### Post by iurisilveira on 2015-02-25
Thank you very much TheFlu, issue resolved!

This page ([http://blog.jdpfu.com/2013/03/01/lin...101-networking]("http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking")[COLOR=#000000] [/COLOR]) gave me the details I needed to resolve the issue.

It was my "resolv.conf" missing dns server addresses. Probably got messes up when I was on VPN the other day and power was cut, somehow the resolv.conf only had my company dns addresses. I added my XFinity DNS servers and.. voila!

Much appreciated*!*

---

### Post by TheFu on 2015-02-25
> **iurisilveira said:**
> Thank you very much TheFlu, issue resolved!

This page ([http://blog.jdpfu.com/2013/03/01/lin...101-networking]("http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking")[COLOR=#000000] [/COLOR]) gave me the details I needed to resolve the issue.

It was my "resolv.conf" missing dns server addresses. Probably got messes up when I was on VPN the other day and power was cut, somehow the resolv.conf only had my company dns addresses. I added my XFinity DNS servers and.. voila!

Much appreciated*!*

With 12.04 and later, do not modify the /etc/resolv.conf file directly.  If you've setup /etc/network/interfaces - use the **dns-nameservers 8.8.8.8** setting. Change to your DNS of choice, of course.  If you are using the GUI to manage networking, then use that.  I think (do not know) that you need to remove the interfaces file and put the resolv.conf back to the way it was.

Glad my article was helpful.

---

