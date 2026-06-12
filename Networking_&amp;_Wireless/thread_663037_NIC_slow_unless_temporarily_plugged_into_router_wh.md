---
title: "NIC slow unless temporarily plugged into router? what?? HEEELP!!"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by senoralastair on 2008-01-09
Hey Ubuntuers!!

I've got a rather strange problem that hopefully one of you networking geniuses will be able to help me solve. I am really quite stumped at the moment.

Basically what's happening is this: I've set up ubuntu server 7.04 on an HP proliant dl360 G2, and am running a squid proxy on it. Until now i thought i had some funny config with the proxy, but it now looks like a network card related thing. 

These are my symptoms: The server is in our corporate lan, and when i try to use it as a proxy, my download speeds are capping at about 40KB/s, when downloading a speedtest file straight from our ISP. Normally these should be downloading at about 800KB/s or so. if i retrieve this same file using wget (on the server), it downloads at full speed! This had me thinking it might be a squid.conf issue, but the following makes me think otherwise...

Yesterday, to test it, i plugged the server directly into an adsl router, and a crossover cable to my lappy for testing with no switches or firewalls in the way. This worked at full speed, which made me start to think it wasn't squid. Once I plugged it back into the corp network (same cable, same NIC, same everything), i then tested the proxy again from my work pc (as i had done previously), and the download speeds were 700-800KB/s!!! 

This morning i tried doing the same thing... i rebooted the server, tested the proxy.. capped me at 40Kb/s, then wired it directly to the adsl router for about a min, then put back as it was, and speeds are around 700Kb/s!!

What on earth is going on? hahaha

Hardware, as previously mentioned is an HP proliant DL360 G2. 
There are 2 onboard NICs, and i've put another netgear gig card in as well for testing purposes (all the same result though).
lspci shows the following for the NICs:

```
01:05.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5701 Gigabit Ethernet (rev 15)
01:06.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5701 Gigabit Ethernet (rev 15)
07:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
```

and the relevant dmesg output:

```
# dmesg | grep eth
[    4.299105] eth0: Tigon3 [partno(233615-001) rev 0105 PHY(5701)] (PCI:66MHz:64-bit) 10/100/1000Base-T Ethernet 00:08:02:a0:a7:36
[    4.299120] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[0]
[    4.299126] eth0: dma_rwctrl[76ff000f] dma_mask[64-bit]
[    5.958482] eth1: Tigon3 [partno(233615-001) rev 0105 PHY(5701)] (PCI:66MHz:64-bit) 10/100/1000Base-T Ethernet 00:08:02:a0:a7:41
[    5.958498] eth1: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[0]
[    5.958503] eth1: dma_rwctrl[76ff000f] dma_mask[64-bit]
[    6.115296] eth2: RTL8169s/8110s at 0xf88c0000, 00:0f:b5:45:42:26, IRQ 19
[    8.714485] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.816346] tg3: eth0: Link is up at 100 Mbps, full duplex.
[    9.816352] tg3: eth0: Flow control is off for TX and off for RX.
[    9.820209] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   19.943109] eth0: no IPv6 routers present
[ 1658.951058] tg3: eth0: Link is down.
[ 1671.180315] r8169: eth2: link up
[ 1681.489830] eth2: no IPv6 routers present
[ 1782.829373] r8169: eth2: link down
[ 1889.660606] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1891.483405] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 1891.483413] tg3: eth0: Flow control is off for TX and off for RX.
[ 1891.487204] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1902.413601] eth0: no IPv6 routers present
[ 1904.843122] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1906.435560] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 1906.435570] tg3: eth0: Flow control is off for TX and off for RX.
[ 1906.439381] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1916.438762] eth0: no IPv6 routers present
[ 1980.996539] tg3: eth0: Link is down.
[ 1985.864268] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 1985.864277] tg3: eth0: Flow control is off for TX and off for RX.
[ 1998.622110] tg3: eth0: Link is down.
[ 2001.904310] r8169: eth2: link up
[ 2121.191207] r8169: eth2: link down
[ 2129.367594] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 2129.367605] tg3: eth0: Flow control is off for TX and off for RX.
[ 2154.940232] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2156.788769] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 2156.788778] tg3: eth0: Flow control is off for TX and off for RX.
[ 2156.792572] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2167.262221] eth0: no IPv6 routers present

```

eth0 is the card i have been using, but the results have been similar on eth2 as well (the netgear card).

If anyone has any suggestions, it'd be the hugest help ever! My boss is back on monday, and i really want this server up and running, as he is wanting to replace it with WINDOWS and ISA Server!!! And we just can't have that, can we!!!

thank you thank you in advance!

---

### Post by saphil on 2008-01-10
Hi!
I have 2 dumb questions.  When you speedtest the network from another computer, does the speedtest read at 800?  Are you sure somebody ELSE on the network hasn't plugged in an old 10MIPS nic carded PC?  Ethernet runs at the speed of the slowest node...

-Wolf

---

### Post by senoralastair on 2008-01-10
ooh.. that's a good point. i asked the senior network engineer and he said it wouldn't be impossible that there could be some old device hiding somewhere in the server racks...
Well spotted! In that code that i printed out with the with the eth0 link speed at 100Mbps, would that stay the same if it was 10Mbps?
And what's weird is that after i plugged into the adsl router, then back into the corp lan, the link speed was reported to be back to 100Mbps, but the download speed through the proxy was still fast.
???

I remember seeing the link speed at 1000Mbps when it was attached to the adsl router, and it said flow control on, full duplex, but on the corp lan it's as below, which is to be expected cos it's plugged into 100meg switches... 


[ 1980.996539] tg3: eth0: Link is down.
[ 1985.864268] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 1985.864277] tg3: eth0: Flow control is off for TX and off for RX.

I'll try attaching it straight into on of the new layer 2 switches, which goes straight onto the big gig switches...

this really is confusing... haha


thanks for the help so far though!! = )

---

### Post by saphil on 2008-01-11
How is the nic pulling that 100mbps? If it is "hard-coded" into the config file, it will probably show as 100mbps regardless of the network flow.  There is also the issue of how many nodes are on the network.  The more you have on there, the more bandwidth is taken up and the slower up and downloads.  There is undoubtably a formula for that, but I cannot remember it.

Have you run etherape on the network?  
```
apt-get install etherape
sudo etherape

```
This is a graphic network traffic application.

If you have had something change on the network, or if your proxyserver box has certain problems, you will probably see the issue.

Does the speed issue change depending upon what day, or time you test?  
If you are on a T1 or other dedicated line, you won't have a bleed from other subscribed clients but on adsl you may have other subscr... no that probably doesn't matter, since a direct link to the modem got 1000mbps...  So I am back to wondering if it is an insider.  If you have a peer-2-peer downloader in the company, etherape will show it (graphically).

---

