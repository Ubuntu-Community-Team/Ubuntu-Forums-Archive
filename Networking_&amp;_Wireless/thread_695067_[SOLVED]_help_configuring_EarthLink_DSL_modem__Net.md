---
title: "[SOLVED] help configuring EarthLink DSL modem / Netgear Ethernet switch"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by kalwisti on 2008-02-12
Hello, This is my first post to the forums.

I recently installed 7.04 Feisty Fawn on my used computer and am having trouble getting my Internet connection configured. I've tried some tips I've found via a forum search, have looked at the Wiki, and have two Ubuntu books from the library (Rickford Grant's "Ubuntu for Non-Geeks" and Marcel Gagne's "Moving to Ubuntu Linux"). Thus far I've had no luck at all ... I'll add here that I'm a bit puzzled why I can't this get to work because the setup described below works fine with PCLinuxOS 2007 and Xandros 4.1 (I multi-boot distros on my Linux box).

Here's a brief description of the setup (all wired, no wireless connections involved):

We have two computers sharing an EarthLink DSL connection: an old iMac and my used Linux computer. The DSL modem (supplied by EarthLink) is a ZyXEL P-600 series (model # P660R-ELNK). Attached to the EarthLink DSL modem is a simple Netgear Ethernet switch (10/100 Mbps, model # FS608 v3). The iMac and used Linux computer are hooked up to the Netgear switch.

The connection protocol is DHCP via a LAN (not DSL PPOE). I think?? (It shows as being configured for DHCP in both Xandros and PCLOS). 

I saw that other users with similar Internet configuration problems were posting info gathered from running several different Terminal commands, so I will include some of that info below. (Almost all of it is Greek / Geek to me). I hope this will help someone more knowledgeable figure out what is going on ...


david@david-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:5A:62:DC:A1  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:5aff:fe62:dca1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14569 (14.2 KiB)  TX bytes:15491 (15.1 KiB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5676 (5.5 KiB)  TX bytes:5676 (5.5 KiB)



david@david-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


david@david-desktop:~$ sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 4541
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:10:5a:62:dc:a1
Sending on   LPF/eth0/00:10:5a:62:dc:a1
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67



david@david-desktop:~$ sudo mii-tool eth0
Password:
eth0: negotiated 100baseTx-FD, link ok



david@david-desktop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:10:5a:62:dc:a1
Sending on   LPF/eth0/00:10:5a:62:dc:a1
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.33 -- renewal in 127325 seconds.



[Below is part of the info produced by $ sudo lshw ]

 *-network DISABLED
             description: Ethernet interface
             product: 3c905B 100BaseTX [Cyclone]
             vendor: 3Com Corporation
             physical id: 8
             bus info: pci@00:08.0
             logical name: eth0
             version: 30
             serial: 00:10:5a:62:dc:a1
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
             resources: ioport:ec00-ec7f iomemory:df018000-df01807f irq:16


It was a struggle to get Ubuntu installed (my fault -- not Ubuntu's -- due to my ignorance of multibooting on two HDs, with  Xandros' LILO as the boot loader), so I would very much like to explore Ubuntu and the GNOME desktop environment. Any help or advice would be greatly appreciated. 

Thank you,
=david

---

### Post by macogw on 2008-02-12
The first command, ifconfig, shows that you're configured correctly.  None of the rest was necessary.  See the IP address it gives?  192.168.1.33?  That's the proper type of IP address to get when behind a router or switch.  If it started with 169 (or maybe it's 161?), then the dhclient would've made sense to run, since that happens when the router isn't talking to you and that's like poking the router and saying "hey you! i'm here!"

Are you still not able to reach the internet?

---

### Post by kalwisti on 2008-02-12
Hi, macogw,

Thanks for taking a look at this and confirming that the ifconfig is OK. When I first saw your reply, I still wasn't able to connect to the Internet but I made one change (described below) and amazingly, it worked. I'm posting this from Ubuntu.

In case this might be useful to someone in the same situation, here's the one change I made:

I started Firefox and typed in the local network (?) URL: [http://192.168.1.1](http://192.168.1.1). 

This brought up the ZyXEL modem's Web-based Configurator (set-up program) in the browser window. 

I took a look at its settings and noticed that under the "Advanced Setup" column, there was a choice labelled "LAN." I clicked on the "LAN" hyperlink and noticed that the boxes for "Primary DNS Server" and "Secondary DNS Server" both had a value of "0.0.0.0."

That looked a bit strange, so I changed those values to the ones which EarthLink's Tech Support staff had originally given us:

Primary DNS Server: 207.69.188.xxx
Secondary DNS Server: 207.69.188.xxy

After making that change, I clicked on the "Apply" button. I restarted Firefox and everything just worked!

I've been using Linux for a little over a year; I still have lots to learn. Networking in particular is an area which borders on The Purely Mystical for me. I did **not** use the Network Settings tool to create a new DSL connection/location; the system created a new connection (??) or somehow auto-configured itself in order to establish the Internet connection. I had made enough unsuccessful attempts that I'm mildly in shock that the connection is working.

That said, could I ask a couple of dumb newbie questions? Do I need to use the Network Settings tool to assign a name to this Internet configuration? Will I need to use the ZyXEL Web-based Configurator to configure the connection on subsequent restarts, or will Ubuntu "remember" the configuration from now on?

Thanks again for your help,
=david

---

### Post by kalwisti on 2008-02-15
Just as a follow-up, the DSL connection works perfectly after shutdown and subsequent restarts ... No need to reconfigure the connection each time.

I have not used the Network Settings tool to assign a name to this configuration. The system hasn't protested about that, either. I will mark this thread as "Solved" for the benefit of future searchers.

=david

---

### Post by Andrew_P on 2008-02-27
The IP addresses of the EarthLink Domain Name Servers (DNS) given by user **kalwisti** are *probably* their standard redirect servers.  If you mistype the URL, they take you to an EarthLink search page with ads, instead of providing the correct 404 error - Page Not Found - possibly breaking various programs that rely on getting the error code from the Web server if they connect to a dead link.

During automated router setup, these are the IPs provided by EarthLink:

207.69.188.196 (West Coast)
207.69.188.197 (East Coast)

EarthLink offers a couple of DNS that behave correctly, generally called their "Opt-Out" DNS, for users who complained bitterly about this treatment of customers and threatened to pull the plug and find another Internet service provider.  They are available, even though EarthLink doesn't endorse their use:

207.69.188.172 (East Coast)
207.69.188.171 (West Coast)

See more on how to use these alternate DNS in this FAQ at the DSLReports forum:
[What are the DNS Opt Out Servers for the Redirecting Earthlink DNS Problem?]("http://www.dslreports.com/faq/earthlink/30_Setup_Installation_and_Configuration#14417") (FAQ #14417)

If you don't want to use EarthLink's DNS, you can also try [OpenDNS.com]("http://www.opendns.com/"), a free service that carries ads, but won't kill the 404 error response:

208.67.222.222
208.67.220.220

I'm currently an EarthLink residential DSL customer, and I've tried EarthLink's standard DNS, their opt-out DNS and the OpenDNS numbers in my modem/router, and all work well, although I presently prefer the EarthLink opt-out DNS.

---

### Post by kalwisti on 2008-02-28
Andrew_P,

Thank you for posting that information about the issue as well as the "opt-out" DNS server alternatives. I looked at those links and although some of the discussion is rather technical, I understand the gist of it. 

We've been EarthLink customers for 8 years; this is the first time I'd heard about the company doing that sort of redirect to the search page with advertisements. (If I saw it in the past, I must not have paid enough attention to be upset by it. IIRC, it is not happening currently ... I get a mostly blank page that says something along the lines of "Server Not Found: Firefox couldn't find the server at www.foo.foo"). 

Although I'm aware that EarthLink has been having financial troubles and had to lay off significant numbers of staff (for whom I'm genuinely sorry), we have generally been satisfied with their residential DSL service. We've seen the company grow over the years, and along with that a downward slide in their customer service. Unfortunately, that seems to be the way of the world ... Our other computer is an old iMac and we noticed that they outsourced their Mac Tech Support to Manila in the Philippines. We don't have to call for help often but when we do, it hasn't been a big problem -- other than the longer time spent on hold.

Thanks again!

---

