---
title: "Internet Connection Sharing Works But Not When Bridging Interfaces"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by marcusgrant on 2008-08-24
Hello,

I am trying to set up my Ubuntu server to be a wireless router but I am currently stuck with the server not being able to share the Internet connection with wired clients when I bridge my Ethernet card with my wireless card. The Ubuntu server can share the Internet connection if I do not set up a bridge and set up NAT on only the Ethernet card.

My Ubuntu server consists of:
- Ubuntu 8.04 LTS for the operating system
- built-in NIC (eth0) for the Ethernet connection
- Atheros-based wireless card (ath0) for the wireless connection
- A PPPOE connection (ppp0) for my ADSL account (for Internet access)
- Linux restricted drivers enabled for madwifi (for the wifi card)
- bridge-utils installed to allow bridging mode
- dhcp3-server installed to allow server to be a DHCP server
- bind9 installed for DNS caching
- hostapd installed to allow the server to be an access point

I do not want to use dnsmasq, firestarter, or any other packages to allow Internet connection sharing.

For my setup, I wanted something like:

[Internet] -- [ppp0e] -- [br0 (eth0 + ath0)] -- [client n (0 to infinity)]

Client computers can connect to the Ubuntu server by either an Ethernet cable connected to the hub or by connecting to the wireless access point.

Since this configuration contained many components, I've opted to install and test things in iterations.

My first iteration was to not configure any wireless and try to share the Internet with only with client computers connected to the network via Ethernet.

My /etc/network/interfaces had only the eth0 interface:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.0.11.1
netmask 255.255.255.0

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up
provider dsl-provider
```

My /etc/default/dhcp3-server was set to use eth0

```

INTERFACES="br0"
```

The script I used to test my iptables setting was set to NAT eth0:

```

# clear existing settings
sudo iptables -F

#logging
sudo iptables -A FORWARD -j LOG --log-level 7 --log-prefix FORWARD
sudo iptables -A INPUT -j LOG --log-level 7 --log-prefix INPUT
sudo iptables -A OUTPUT -j LOG --log-level 7 --log-prefix OUTPUT
sudo iptables -t nat -A POSTROUTING -j LOG --log-level 7 --log-prefix POSTROUTING
sudo iptables -t nat -A PREROUTING -j LOG --log-level 7 --log-prefix PREROUTING
sudo iptables -t nat -A OUTPUT -j LOG --log-level 7 --log-prefix OUTPUT-ROUTING

sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A INPUT -m state --state NEW -i ! ppp0 -j ACCEPT
# only if both of the above rules succeed, use
sudo iptables -P INPUT DROP

sudo iptables -A FORWARD -i ppp0 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A FORWARD -i eth0 -o ppp0 -j ACCEPT

sudo iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
sudo iptables -A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu 
sudo iptables -A FORWARD -i ppp0 -o ppp0 -j REJECT

# Allow forwarding
sudo sysctl -w net.ipv4.ip_forward=1
```

My /etc/ppp/peers/dsl-provider was set to use eth0 also:

```

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
#persist
#maxfail 0
#holdoff 20
plugin rp-pppoe.so eth0
nic-eth0
user "user@domain.com"
```

In this setup, my wired client computer was able to surf the Internet with no problems.

When I ping a website and tail -f syslog, I get the following log entries from iptables:

```

Aug 23 22:06:31 snuth kernel: [  463.865448] PREROUTINGIN=eth0 OUT= MAC=[removed] SRC=10.0.11.49 DST=206.190.60.37 LEN=60 TOS=0x00 PREC=0x00 TTL=128 ID=9771 PROTO=ICMP TYPE=8 CODE=0 ID=512 SEQ=23040 
Aug 23 22:06:31 snuth kernel: [  463.865480] FORWARDIN=eth0 OUT=ppp0 SRC=10.0.11.49 DST=206.190.60.37 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=9771 PROTO=ICMP TYPE=8 CODE=0 ID=512 SEQ=23040 
Aug 23 22:06:31 snuth kernel: [  463.865492] POSTROUTINGIN= OUT=ppp0 SRC=10.0.11.49 DST=206.190.60.37 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=9771 PROTO=ICMP TYPE=8 CODE=0 ID=512 SEQ=23040 
Aug 23 22:06:31 snuth kernel: [  463.894159] FORWARDIN=ppp0 OUT=eth0 SRC=206.190.60.37 DST=10.0.11.49 LEN=60 TOS=0x00 PREC=0x00 TTL=49 ID=27902 PROTO=ICMP TYPE=0 CODE=0 ID=512 SEQ=23040 
```


For the second iteration, I tried to bridge the Ethernet interface with the wireless interface.

My /etc/network/interfaces now have settings for eth0 and br0

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto ath0
iface ath0 inet manual
pre-up wlanconfig ath0 create wlandev wifi0 wlanmode ap
post-down wlanconfig ath0 destroy

auto br0
iface br0 inet static
address 10.0.11.1
network 10.0.11.0
netmask 255.255.255.0
broadcast 10.0.11.255
bridge_ports eth0 ath0

auto dsl-provider
iface dsl-provider inet ppp

pre-up /sbin/ifconfig eth0 up
pre-up /sbin/ifconfig ath0 up
pre-up /sbin/ifconfig br0 up # line maintained by pppoeconf
provider dsl-provider

```

My /etc/default/dhcp3-server was modified to look at br0

```

INTERFACES="br0"
```

And my iptables script was slightly modified to look at br0 instead of eth0:

```

# clear existing settings
sudo iptables -F

#logging
sudo iptables -A FORWARD -j LOG --log-level 7 --log-prefix FORWARD
sudo iptables -A INPUT -j LOG --log-level 7 --log-prefix INPUT
sudo iptables -A OUTPUT -j LOG --log-level 7 --log-prefix OUTPUT
sudo iptables -t nat -A POSTROUTING -j LOG --log-level 7 --log-prefix POSTROUTING
sudo iptables -t nat -A PREROUTING -j LOG --log-level 7 --log-prefix PREROUTING
sudo iptables -t nat -A OUTPUT -j LOG --log-level 7 --log-prefix OUTPUT-ROUTING

sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A INPUT -m state --state NEW -i ! ppp0 -j ACCEPT
# only if both of the above rules succeed, use
sudo iptables -P INPUT DROP

sudo iptables -A FORWARD -i ppp0 -o br0 -m state --state ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A FORWARD -i br0 -o ppp0 -j ACCEPT

sudo iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
sudo iptables -A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu 
sudo iptables -A FORWARD -i ppp0 -o ppp0 -j REJECT

# Allow forwarding
sudo sysctl -w net.ipv4.ip_forward=1
```

My /etc/ppp/peers/dsl-provider was modified to use br0 also:

```

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
#persist
#maxfail 0
#holdoff 20
plugin rp-pppoe.so br0
nic-br0
user "user@domain.com"
```

Now when I ping the same website and tail -f syslog, I only get:

```

Aug 23 23:43:56 snuth kernel: [ 1637.252665] PREROUTINGIN=br0 OUT= PHYSIN=eth0 MAC=[removed] SRC=10.0.11.49 DST=206.190.60.37 LEN=60 TOS=0x00 PREC=0x00 TTL=128 ID=11744 PROTO=ICMP TYPE=8 CODE=0 ID=512 SEQ=29696 
Aug 23 23:43:56 snuth kernel: [ 1637.252706] FORWARDIN=br0 OUT=ppp0 PHYSIN=eth0 SRC=10.0.11.49 DST=206.190.60.37 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=11744 PROTO=ICMP TYPE=8 CODE=0 ID=512 SEQ=29696 
Aug 23 23:43:56 snuth kernel: [ 1637.252719] POSTROUTINGIN= OUT=ppp0 PHYSIN=eth0 SRC=10.0.11.49 DST=206.190.60.37 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=11744 PROTO=ICMP TYPE=8 CODE=0 ID=512 SEQ=29696 
```

Notice how for this set of entries, there is no fourth entry (a FORWARD entry). My client computer times out on waiting for the ping reply.

I haven't tried to change any configuration for the wifi portion yet because I was hoping that the wired clients would have been able to still access the Internet.

Can anybody help me figure out what's wrong? I've been ransacking my brain for the past few weeks. I had a similar setup last year (using Edgy) and it worked fine. Wired clients and wireless clients were able to access the Internet from the Ubuntu server. I failed to save off my old configuration when I opted to upgrade some hardware and change my file system :-(.

Please help,
Marcus

---

### Post by SpaceTeddy on 2008-08-24
i personally would choose a routed setup... but - that is me...
Also, before i start - thank you for providing lots of info. It saves me asking for it :)

So, now to the case. From your little diagram i gather that eth0 and ath0 are both in the same computer, and that the ppp0 device is being overlayed by the ppp0 device. In this case, you cannot bridge eth0 and ath0 together, as it would imply that any client in your private network would need it's own internet ip address. But you only have one (the ppp0 device). so you will need to use the "normal" way of masquerading the traffic... at least i do not see any other way.

As i understand bridging - you make two or more network devices act as one. But that is not what you want to do here. You want to have a privte network on ath0 and a ppp0 connection on eth0. It could be possible to run the dialup through a switch and double use the eth0 device - but that would mean that anyone can look into your network. I'd suggest getting a second network card and using that purely for the dialup...

mhm - come to think of it - it could work. But i think you need to put ath0 as well as eth0 in promisc mode, so that ANY packet they receive will be handed to the br0 device. This is a sample config for a bridged network card that comes up in promisc mode (taken from this [[COLOR="Blue"]tutotial[/COLOR]]("http://ubuntuforums.org/showthread.php?t=752127")):
```
auto eth1
iface eth1 inet manual
up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down
```

maybe that helps with your setup... 

hope it helps :)

---

### Post by ebischoff on 2009-06-12
Same problem here. I'm trying to replace eth0 with br0 (purpose is to have br0 = eth0 + tap0), but masqueraded local network computers can't access the Internet anymore.

My configuration is much simpler than the first one mentioned here but the problem is exactly the same.

I am running Kubuntu jaunty jackalope, and package ppp (including roaring penguin PPPoE plugin) is version 2.4.5.
 
Here is my /etc/network/interfaces:
```

  auto lo
  iface lo inet loopback

  auto eth0
  iface eth0 inet manual

  auto br0
  iface br0 inet static
        bridge_ports eth0
        bridge_stp off
        bridge_maxwait 0
        address 10.0.0.140
        netmask 255.0.0.0
        network 10.0.0.0
        broadcast 10.255.255.255

  auto nerim
  iface nerim inet ppp
  provider nerim
      pre-up /sbin/ifconfig br0 up # line maintained by pppoeconf

```

/etc/ppp/peers/nerim has been modified to use br0 instead of eth0
```

  noipdefault
  defaultroute
  replacedefaultroute
  hide-password
  noauth
  persist
  mtu 1492
  plugin rp-pppoe.so br0
  user "ebischoff@adslc.nerim.nerim"
  usepeerdns
  ipv6 ,

```

I tried to put the Ethernet card interface eth0 in promiscuous mode as suggested above, but it did not help.

I logged the packets coming back from the Internet and I noticed that they arrive on interface "br0" instead of "ppp0". Here is the normal situation (PPPoE over eth0) as analyzed by an iptables rules with LOG target:
```

Jun 12 08:21:48 ns kernel: [26325.717776] IN=ppp0 OUT=
MAC= SRC=62.4.16.99 
DST=213.41.243.33 LEN=64 TOS=0x00 PREC=0x00 TTL=61 ID=33728 DF PROTO=TCP SPT=80
DPT=57026 WINDOW=65535 RES=0x00 ACK SYN URGP=0          

```

And here is the problematic situation (PPPoE over br0):
```

Jun 11 23:50:30 ns kernel: [22485.499333] IN=br0 OUT= PHYSIN=eth0
MAC=00:1d:60:fc:58:1d:00:e0:fc:47:10:22:88:64 SRC=212.95.66.20
DST=213.41.243.33 LEN=60 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=TCP SPT=80
DPT=56875 WINDOW=5792 RES=0x00 ACK SYN URGP=0

```

Notice it should be *IN=ppp0* and not *IN=br0*. Maybe this information helps.

Is there some incompatibility between bridging and PPPoE? Any thoughts?

---

### Post by ebischoff on 2009-08-21
As this problem affects all linux distributions and not only (K)Ubuntu, the technical discussion and search for a workaround or for a real solution is continuing on the 
[RP-PPPoE mailing list at Roaring Penguin]("http://lists.roaringpenguin.com/cgi-bin/mailman/listinfo/rp-pppoe").

See also this thread:
[http://kerneltrap.org/mailarchive/linux-net/2009/8/19/6329993](http://kerneltrap.org/mailarchive/linux-net/2009/8/19/6329993)

If we reach some results it will of course be announced here.

---

### Post by ebischoff on 2009-08-22
Pascal Hambourg suggested the following workaround:

# echo 0 > /proc/sys/net/bridge/bridge-nf-filter-pppoe-tagged

and it works wonderfully here at my place.

Pascal explained to me the reason of the problem : filtering in bridges have strange side effects. The kernel parameter above disables filtering in bridges.

Pascal also told me that, as of kernel 2.6.29, this kernel parameter will be set to 0 by default. So, when (K)Ubuntu will move to 2.6.29 kernels, the problem will not appear spontaneously anymore.

A real fix would be to have bridge-nf (the association of bridging and netfilter) not conflict with PPPoE, but only the bridging gurus can fix that, and I suppose it is far from being obvious.

---

### Post by ebischoff on 2009-10-08
Hi all,

Bart De Schuymer has come up with a patch to br_netfilter that should solve the problem. Here is what Bart writes:

------------------------------------------------------------------
I finally had time to dig into this. The attached patch should fix 
things. As was pointed out above, IP DNAT on bridged traffic didn't work for VLAN.

I only tested the VLAN situation, so an ack that it fixes the pppoe situation would be nice. I'll send the patch to the netfilter-devel list shortly.

By the way, I have the impression that most people on the 
netfilter-devel mailing list seem to be unaware of the benefits of 
transparent IP NAT on a bridge, so I'd be grateful if you and others promote this functionality when you have the opportunity!

The patch also makes the DNAT more transparent: the souce MAC address is no longer changed to the MAC address of the bridge device.
------------------------------------------------------------------

I hope that helps,

---

