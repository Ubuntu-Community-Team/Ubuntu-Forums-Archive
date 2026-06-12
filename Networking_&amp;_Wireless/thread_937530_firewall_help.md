---
title: "firewall help"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by kiminaiseah on 2008-10-03
hi everyone, i am ask for some assistant to solve my problem. i was resolving this problem for about 3months,

btw. i have a test machine(server) which has 3 interface, eth0 = local network, acts as my local's network gateway, dhcp server. eth1 = isp1, eth2 = isp2. both isp balances tcp/udp traffic around my network . my test machine(server) has a services, zabbix, smtp server. my dilemma is when my server's route also been balanced alternate outgoing traffic to eth1 and eth2. so my ip in eth2 has been put spamlist. 

i am asking here it would be possible to separate or use only one route to my server going outside, with load balance capable with my local network. 

i was using shorewall 4.0.13 

my conf examples

/etc/shorewall/masq
###############################################################################
#INTERFACE              SOURCE          ADDRESS         PROTO   PORT(S) IPSEC  $
eth1    eth0
eth2    eth0
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE


/etc/shorewall/interfaces
###############################################################################
#ZONE   INTERFACE       BROADCAST       OPTIONS
loc     eth0
net1    eth1
net2   	eth2
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE


/etc/shorewall/providers
############################################################################################
#NAME   NUMBER  MARK    DUPLICATE       INTERFACE       GATEWAY         OPTIONS         COPY
isp1    1       1       main    eth1    xxx.xxx.xxx.100 track,balance    eth0
isp2	2       2       main    eth2    xxx.xxx.100.xxx	track,balance    eth0
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE


/etc/shorewall/rules
############################################################################################################################
#ACTION         SOURCE          DEST            PROTO   DEST    SOURCE          ORIGINAL        RATE            USER/   MARK
#                                                       PORT    PORT(S)         DEST            LIMIT           GROUP
#SECTION ESTABLISHED
#SECTION RELATED
SECTION NEW

ACCEPT	all	all
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE


/etc/shorewall/policy
###############################################################################
#SOURCE         DEST            POLICY          LOG             LIMIT:BURST
#  
all	all	ACCEPT
#LAST LINE -- DO NOT REMOVE




# ip route show
xxx.xxx.xxx.100/29 dev eth1  proto kernel  scope link  src xxx.xxx.xxx.100
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.60
xxx.xxx.100.xxx/24 dev eth2  proto kernel  scope link  src xxx.xxx.100.xxx
default
        nexthop via xxx.xxx.xxx.100  dev eth1 weight 1
        nexthop via xxx.xxx.100.xxx  dev eth2 weight 1

---

