---
title: "[SOLVED] PPPoE via ADSL router"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by tomski on 2008-09-04
Hi there,

Hope someone out there may be able to help me

i have a ZyXel P660R-61C adsl router & a ubuntu hardy 8.4.1 server

i am currently trying to get my ubuntu server to act as the firewall/gateway/webserver for my home network

what i want to do is set the adsl router in bridge mode using RFC1483 with LLC 0,38 with PPPoE passthrough enabled, NAT turned off, DHCP turned off and have the ubuntu server collect the WAN IP via the ZyXEL bridge.

i have tried this configuration using an ethernet zyxel router P334 as this has a PPPoE client built into it & it works.

My problem is that i cant seem to get my ubuntu server to login even with the correct details or BT TEST ACCOUNT:
bt_test_user@startup_domain

My ubuntu server has 3 nic's:
eth0 WAN ----> ZyXEL P660R-61C adsl router/bridge
eth1 LAN ----> 8 port switch 
eth2 DMZ ----> ethernet wireless AP (not connected yet)
it is running shorewall, apache2, MySql, mldonkey(deamon)

when i use the network icon on the top panel to setup the pppoe client it refuses to bind to eth0 & always defaults to eth2!!!
i went a bit lateral and thought ok lets connect eth2 to my adsl bridge but still it refused to connect but this time it defaulted to eth1????????????????

When i try to use ```
pppoeconf
``` it cannot find a PPPoE concentrator?

I know the adsl router works as a PPPoE passthrough when setup this way & i know my isp support PPPoE connections.

I hope someone out there has tried a similar setup & can give some kind of advice as i'd love to make this work because im currently in a double nat situation which can affect vpn connectivity & other issue's plus it's just wrong

---

### Post by Kylibar on 2008-11-21
hey there, had sugery on my hand today, so please 4give for typos

this is a good format for PPPoE bridge when eth0-2 are not bridged

[HTML]
auto lo
iface lo inet loopback
#
auto eth0
iface eth0 inet static
address		x.x.x.x
gateway		x.x.x.x
netmask		x.x.x.x
	up ifup ppp0
	down ifdown ppp0
#
auto eth1
iface eth1 inet static
address		x.x.x.x
netmask		x.x.x.x
#
auto eth2
iface eth2 inet static
address		x.x.x.x
netmask		x.x.x.x
#
auto ppp0
iface ppp0 inet ppp
provider	dsl-provider
[/HTML]

when you run pppoeconf (assuming eth0 in your system is connected directly to the modem) run like this;

[HTML]
pppoeconf eth0
[/HTML]

ok so you ARE running shorewall 3iface system.

im not writing that unless im sure ur gonna read it(1 handed right now).  is this a dead thread? im running a 3iface shorewall w/ PPPoE bridge

---

### Post by tomski on 2008-11-21
Hi there Kylibar

many many thanks for your response & i hope your hand get's better soon!


i have been seriously busy of recent therefore i have been unable to post a response to this but i have partialy resolved this issue in that it is working with a config similar to the one you posted

i realised my problem was that the adsl router & eth0 still need a private /24 to communicate 
so dsl router has: 192.168.2.1 eth0 has: 192.168.2.10
when i configured the files with all the relevant details i then type pon & hey presto it all worked fine.

there was me thinking the dsl router & eth0 would use multicast to communicate but this was not the case!

i have since disabled pppoe passthrough & i now connect using MPOA (Multi Protocol over ATM) so it would appear that BT actually allow for some advanced configurations to be used but this may be because the ADSL service is provided via an ISP that use BT wholesale.

i will make this thread as resolved but i will at some point post up all config's i have used for this so as to help others trying to achive this.

once again many thnx Kylibar for the response Kudos to you my friend

---

