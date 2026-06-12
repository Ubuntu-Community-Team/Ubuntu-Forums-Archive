---
title: "dhclient overwrites my /etc/resolv.conf"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by stnever on 2007-04-14
Hello,

I have managed to get my internet connection up and running (and shared). I configured the connection via pppoeconf, and then used pon dsl-provider to start it.

At this time, my ISP sends me an IP address and two DNS server addresses. All works fine. However after 30min the file /etc/resolv.conf gets overwritten with a new dns ( 10.0.0.138 ).

I understand that it's telling me to use the modem as a dns forwarder, but it doesn't work (pinging IPs work fine, DNS lookups fail).

Now, I already know the IP address of my preferred DNS server. But I can't stop /etc/resolv.conf from being overwritten. I have tried:

[LIST]
[*]editing /etc/dhcp3/dhclient.conf and remove "domain-name-servers" from the "request" line
[*]editing the same file and adding "prepend domain-name-servers X.X.X.X;" (my preferred DNS)
[/LIST]

The file still gets overwritten. I can see three daemons in the background (one dhclient for each interface eth0, eth1, eth2).

Question is: are those daemons reading the conf file? Do I need to "restart" them? Should there be a dhclient for each interface? (eth2 is unplugged, eth1 is the local network which shares this computer's connection, and eth0 is the connection to my DSL modem -- the connection in itself is ppp0, should I have a daemon here as well?)

Please help... any other info I can give you?

---

### Post by kidders on 2007-04-15
Hi there,

Overwriting resolv.conf based on DHCP-provided information is almost always the right thing for a Linux box to do. Having said that, I often get quite frustrated trying to *stop* it happening, when there's a setting I want to override. You're taking the correct approach ... it really *should* work, except that there is probably something you're overlooking (which is easy, given the number of DHCP clients you're running!).

I often wind up resorting to hacking the network interface configuration scripts (ie deleting the bits that handle resolv.conf rewrites), simply because it's easier than trying to figure out what I've missed! If you're using Ext3, another (similarly hacky) alternative would be to take a look at the extended file attributes available to you. There is one that will let you make a file immutable, so not even root can rewrite it.

Another way of chickening out and avoiding the problem would be to investigate why your modem's DNS server won't do its job properly.

---

### Post by stnever on 2007-04-15
Hi, thanks for answering!

> You're taking the correct approach ... it really should work, except that there is probably something you're overlooking (which is easy, given the number of DHCP clients you're running!).

Yes, I think that's the problem. I have these three processes running:

> 
stnever@tenshimaru:~$ ps aux | grep dhc
dhcp      3487  0.0  0.1   2392   852 ?        S<s  Apr14   0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
dhcp      8409  0.0  0.1   2392   736 ?        S<s  Apr14   0:00 dhclient3 -pf /var/run/dhclient.eth1.pid -lf /var/lib/dhcp3/dhclient.eth1.leases eth1
dhcp      8455  0.0  0.1   2392   748 ?        S<s  Apr14   0:00 dhclient3 -pf /var/run/dhclient.eth2.pid -lf /var/lib/dhcp3/dhclient.eth2.leases eth2
stnever  12989  0.0  0.1   2796   748 pts/0    R+   07:36   0:00 grep dhc


I have three ethernet cards (eth0, connected to the modem; eth1, connected to my local network; and eth2, disconnected). Since I use DSL, ifconfig reports a ppp0 connection (actually ppp1 here because I killed an old one):

> 
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:10.0.0.1  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::2e0:7dff:fed1:1d81/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1168270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1079128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:5246 txqueuelen:1000 
          RX bytes:917114147 (874.6 MiB)  TX bytes:547578475 (522.2 MiB)
          Interrupt:193 Base address:0x4c00 

eth1      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:192.168.20.1  Bcast:192.168.20.255  Mask:255.255.255.0
          inet6 addr: fe80::200:b4ff:fec4:32f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1059156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1122867 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:536209632 (511.3 MiB)  TX bytes:828518389 (790.1 MiB)
          Interrupt:201 Base address:0x6800 

eth2      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Base address:0xc400 

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:201.27.161.11  P-t-P:200.204.210.247  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1160414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1073010 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:890955821 (849.6 MiB)  TX bytes:523573752 (499.3 MiB)



On which of those should I run dhclient? I suppose eth2 and eth1 aren't necessary, but is it correct to run on eth0, or should it run on ppp0 (does that even make sense?)

TIA!

---

### Post by kidders on 2007-04-16
Hey again,

You should run a DHCP client on any interface you're interested in using, that is connected to a network with a DHCP *server* running on it.

[B]eth0
[/B]Without this interface, you would probably be unable to communicate directly with your modem. It appears be be successfully acquiring a DHCP-assigned address, although any DNS server address it configures would most likely be useless.

[B]eth1
[/B]This network also seems to be assigning you an address, without which you would have no access to it.

[B]eth2
[/B]The DHCP client on this interface is failing (which may be causing a short delay at boot-time). If you don't intend to use this network card, you could deconfigure it ... however, since no DHCP server is operating here, no resolv.conf rewrites are being performed, so it wouldn't simplify your problem.

**ppp1**
Disabling the DHCP client on this interface would deny you internet access over this interface.


It looks as though your DNS problems may be the result of instructions received from the DHCP server on the eth0 network. This is irritating the *hell* out of me, because I don't seem to be able to find a way to _ignore_ those settings ... only ways of _overriding_ them. Grrrrrr! ](*,) The problem is that you really don't know what to override them with. I've been wandering through man pages for a while with no success, but the answer **has** to be in there somewhere!

> Another way of chickening out and avoiding the problem would be to investigate why your modem's DNS server won't do its job properly.Scratch that suggestion ... it was based on a faulty assumption about your network configuration, which the additional detail you posted cleared up. Sorry. The way to solve your problem is to find some way of telling Ubuntu to pay attention to the search domain/DNS/etc. settings provided over ppp0 **only** ... if I could just figure out how hehe!

Also, you may want to edit your last post. Many people consider their MAC addresses private, and don't like to freely disclose them. If that matters to you, you should maybe blank them out with 00's.

---

### Post by stnever on 2007-04-16
I *think* I got it working, I edited my /etc/dhcp3/dhclient.conf:

> 
# I added this to make this server my preferred dns
prepend domain-name-servers 200.184.26.3;

# I removed domain-name-servers from this list
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, host-name,
        netbios-name-servers, netbios-scope;


Wasn't working at first, but after a reboot, the file is still being overwritten, but now with the values I specified (I know that because I made a typo on that dns address and had to fix it manually again every 30min).

Now, I still don't know where should dhclient run.

> 
eth0
Without this interface, you would probably be unable to communicate directly with your modem. It appears be be successfully acquiring a DHCP-assigned address, although any DNS server address it configures would most likely be useless.

That makes sense, although it is connected to my DSL modem and seems the IP never changes. I'll keep the daemon here.

> eth1
This network also seems to be assigning you an address, without which you would have no access to it.
I configured that address manually via ifconfig eth1 192.168.20.1 . This is the card that is connected to my hub, and thus local network. I think I can kill the daemon here then.

> 
eth2
The DHCP client on this interface is failing (which may be causing a short delay at boot-time). If you don't intend to use this network card, you could deconfigure it ... however, since no DHCP server is operating here, no resolv.conf rewrites are being performed, so it wouldn't simplify your problem.
Yes, this is an onboard ethernet socket which I'm not currently using. I think I'll kill the daemon here as well.


> ppp1
Disabling the DHCP client on this interface would deny you internet access over this interface.

This is where it gets weird... ps aux | grep dhc only caught the three daemons in my previous post, seems like there are NO dhclients listening on this interface :shock: But things are working...

Thanks for the help! But, I'd like to know more about this, don't stop now just because it's working! :D

---

### Post by kidders on 2007-04-16
Hmm... I was hoping to find a way to avoid overriding your DNS server settings like that. This way, you'll have to manually correct your DNS server addresses if/when your ISP changes them, and will lose out on any load balancing your ISP may be doing that could improve performance.

> **stnever said:**
> Now, I still don't know where should dhclient run.I should point out that there isn't really any reason to try to avoid using DHCP.

> **stnever said:**
> seems like there are NO dhclients listening on this interfaceThat's possible. DHCP isn't the only protocol capable of handling IP address assignment. PPP can (and often *needs* to) do it too ... so nothing to worry about there.

---

