---
title: "eth0 up but not working - dropped: exponential"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by dualboot on 2008-07-13
Hi All,
My eth0 has stopped working, and I'm exhausted my troubleshooting abilities.:(  

It is a 10/100/1000 card, with RTL8169S-32 on the chip.  

ifconfig shows zero for all the traffic stats except dropped which is crazy (I repeated the command as quick as I could hit up arrow, return and the difference was over 8 billion !!!!!!)

I've tried rebooting and re-seating the card.  I've changed the cable and switch port (its not showing any traffic, but the link comes up)

The only change I've made that I've made recently was to add a port to my Guarddog firewall to allow bittorrent to connect (on eth2 my internet link).  I have tried disabling the firewall in Guarddog, but no good. 

I've pasted some info below that might mean something to someone - any ideas ? (or suggestions for good troubleshooting resources ?)

ifconfig:

root@justin-desktop:/home/justin# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:0b:2b:15:8a:01  
          inet addr:10.1.1.201  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:2bff:fe15:8a01/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:14985140892255 overruns:0 frame:0
          TX packets:0 errors:0 dropped:184 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0x8000 

ethtool:

root@justin-desktop:/home/justin# ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: pumbg
	Current message level: 0x00000033 (51)
	Link detected: yes

grep of dmesg for eth0

root@justin-desktop:/home/justin# grep eth0 dmesg.txt 
[   28.406666] eth0: RTL8110s at 0xffffc20000328000, 00:0b:2b:15:8a:01, XID 04000000 IRQ 19
[   51.962539] r8169: eth0: link up
[   60.729744] DROPPED IN= OUT=eth0 SRC=10.1.1.201 DST=224.0.0.22 LEN=40 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF OPT (94040000) PROTO=2 
[   60.889684] DROPPED IN= OUT=eth0 SRC=10.1.1.201 DST=224.0.0.22 LEN=40 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF OPT (94040000) PROTO=2 
[   60.921999] DROPPED IN= OUT=eth0 SRC=10.1.1.201 DST=224.0.0.251 LEN=266 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=246 
[   61.173901] DROPPED IN= OUT=eth0 SRC=10.1.1.201 DST=224.0.0.251 LEN=266 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=246 
[   65.952464] bridge-eth0: enabling the bridge
[   65.952468] bridge-eth0: up
[   65.952469] bridge-eth0: already up
[   65.952472] bridge-eth0: attached
[   68.413635] eth0: no IPv6 routers present
[   85.755342] LIMITED IN= OUT=eth0 SRC=10.1.1.201 DST=224.0.0.251 LEN=151 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=131 
[   88.341722] DROPPED IN= OUT=eth0 SRC=10.1.1.201 DST=224.0.0.251 LEN=240 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=220 
[  100.970498] DROPPED IN= OUT=eth0 SRC=10.1.1.201 DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48 
[  107.997089] NETDEV WATCHDOG: eth0: transmit timed out
[  108.405085] r8169: eth0: link up
[  121.371008] DROPPED IN= OUT=eth0 SRC=10.1.1.201 DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48 
[  158.574135] DROPPED IN= OUT=eth0 SRC=10.1.1.201 DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48 
[  195.495278] bridge-eth0: disabling the bridge
[  195.498925] bridge-eth0: down
[  195.499087] bridge-eth0: detached
[  197.084833] r8169: eth0: link up
[  197.086220] bridge-eth0: enabling the bridge
[  197.086224] bridge-eth0: up
[  197.086225] bridge-eth0: already up
[  197.086227] bridge-eth0: attached
[  202.298626] eth0: no IPv6 routers present
[  215.122338] DROPPED IN= OUT=eth0 SRC=10.1.1.201 DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48 
[  231.121818] DROPPED IN= OUT=eth0 SRC=10.1.1.201 DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48 
[  253.649049] NETDEV WATCHDOG: eth0: transmit timed out
[  254.057045] r8169: eth0: link up
[  263.122787] DROPPED IN= OUT=eth0 SRC=10.1.1.201 DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48 
[  327.122722] DROPPED IN= OUT=eth0 SRC=10.1.1.201 DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48 
root@justin-desktop:/home/justin#

---

### Post by dualboot on 2008-07-13
Gnome-nettool says lists eth0 but when you click configure it says it does not exist.

I can't think why it has suddenly gone like this ?

---

