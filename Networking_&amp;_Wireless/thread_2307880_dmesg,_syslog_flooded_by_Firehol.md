---
title: "dmesg, syslog flooded by Firehol"
date: 2015-12-29
forum: Networking &amp; Wireless
---

### Post by CrimsonRider on 2015-12-29
I've been running a firehol firewall for many years, but since I upgraded to 15.10 my dmesg and syslog are filling to the brim with these;
```

[Tue Dec 29 11:52:40 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=95.101.203.240 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=60 ID=10038 DF PROTO=TCP SPT=80 DPT=57036 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:53:02 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=74.125.136.156 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=50 ID=49737 PROTO=TCP SPT=443 DPT=49443 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:53:14 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=74.125.136.17 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=50 ID=64713 PROTO=TCP SPT=443 DPT=54200 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:53:14 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=74.125.136.17 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=50 ID=64714 PROTO=TCP SPT=443 DPT=54200 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:53:59 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=74.125.136.139 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=50 ID=33101 PROTO=TCP SPT=443 DPT=49439 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:54:49 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=74.125.136.102 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=50 ID=30637 PROTO=TCP SPT=443 DPT=49501 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:54:49 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=74.125.136.102 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=50 ID=30638 PROTO=TCP SPT=443 DPT=49501 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:55:19 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=71.192.24.195 DST=83.84.30.242 LEN=40 TOS=0x00 PREC=0x00 TTL=241 ID=29116 PROTO=TCP SPT=52656 DPT=51300 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:55:39 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=74.125.136.94 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=50 ID=33775 PROTO=TCP SPT=443 DPT=49495 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:56:03 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=74.125.136.138 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=50 ID=8689 PROTO=TCP SPT=443 DPT=49507 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:56:16 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=74.125.136.189 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=50 ID=34544 PROTO=TCP SPT=443 DPT=49511 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:56:34 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=74.125.206.101 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=48 ID=50021 PROTO=TCP SPT=443 DPT=49500 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:56:36 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=31.13.91.6 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=90 ID=42983 DF PROTO=TCP SPT=443 DPT=49525 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:56:36 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=31.13.91.6 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=90 ID=42984 DF PROTO=TCP SPT=443 DPT=49525 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:57:54 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=74.125.136.97 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=50 ID=4828 PROTO=TCP SPT=443 DPT=49541 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:57:56 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=74.125.136.157 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=50 ID=15 PROTO=TCP SPT=443 DPT=49549 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:57:56 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=74.125.136.157 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=50 ID=16 PROTO=TCP SPT=443 DPT=49549 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:57:57 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=74.125.136.94 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=50 ID=50559 PROTO=TCP SPT=443 DPT=49554 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:57:57 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=74.125.136.94 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=50 ID=50560 PROTO=TCP SPT=443 DPT=49554 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:58:00 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=74.125.136.95 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=50 ID=43799 PROTO=TCP SPT=443 DPT=49531 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:58:00 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=74.125.136.95 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=50 ID=43800 PROTO=TCP SPT=443 DPT=49531 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:58:00 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=74.125.136.95 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=50 ID=43801 PROTO=TCP SPT=443 DPT=49531 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:59:35 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=31.13.91.6 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=90 ID=60184 DF PROTO=TCP SPT=443 DPT=49524 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:59:35 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=31.13.91.6 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=90 ID=60185 DF PROTO=TCP SPT=443 DPT=49524 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 11:59:54 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=118.216.68.27 DST=83.84.30.242 LEN=160 TOS=0x00 PREC=0x00 TTL=42 ID=56840 PROTO=ICMP TYPE=3 CODE=1 [SRC=83.84.30.242 DST=192.168.10.4 LEN=132 TOS=0x00 PREC=0x00 TTL=47 ID=57943 PROTO=UDP SPT=51300 DPT=52756 LEN=112 ]
[Tue Dec 29 12:01:27 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=74.125.136.189 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=50 ID=47907 PROTO=TCP SPT=443 DPT=49564 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 12:01:27 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=74.125.136.189 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=50 ID=47908 PROTO=TCP SPT=443 DPT=49564 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 12:01:27 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=74.125.136.189 DST=83.84.30.242 LEN=40 TOS=0x08 PREC=0x40 TTL=50 ID=47909 PROTO=TCP SPT=443 DPT=49564 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 12:01:56 2015] PASS-unknown:IN=br0 OUT=eth4 MAC=00:1b:21:09:ef:5a:64:27:37:19:66:42:08:00 SRC=192.168.40.54 DST=52.22.204.30 LEN=40 TOS=0x00 PREC=0x00 TTL=127 ID=8052 DF PROTO=TCP SPT=64794 DPT=443 WINDOW=0 RES=0x00 ACK RST URGP=0
[Tue Dec 29 12:02:22 2015] IN-InetZiggo:IN=eth4 OUT= MAC=bc:5f:f4:1c:90:b4:00:01:5c:6c:7c:46:08:00 SRC=61.221.180.55 DST=83.84.30.242 LEN=40 TOS=0x00 PREC=0x00 TTL=239 ID=0 DF PROTO=TCP SPT=59610 DPT=51300 WINDOW=0 RES=0x00 RST URGP=0
[Tue Dec 29 12:03:29 2015] PASS-unknown:IN=br0 OUT=eth4 MAC=00:1b:21:09:ef:5a:64:27:37:19:66:42:08:00 SRC=192.168.40.54 DST=54.230.13.39 LEN=40 TOS=0x00 PREC=0x00 TTL=127 ID=21253 DF PROTO=TCP SPT=49419 DPT=443 WINDOW=0 RES=0x00 ACK RST URGP=0
```

And I don't know why. 
Take for instance this;

```
PASS-unknown:IN=br0 OUT=eth4 MAC=00:1b:21:09:ef:5a:64:27:37:19:66:42:08:00 SRC=192.168.40.54 DST=54.230.13.39 LEN=40 TOS=0x00 PREC=0x00 TTL=127 ID=21253 DF PROTO=TCP SPT=49419 DPT=443 WINDOW=0 RES=0x00 ACK RST URGP=0
```

This seems to be a packet for a HTTPS site at 52.230.13.39, from the bridge br0 on the LAN, going via eth4 to the internet. Why would that show up in dmesg?

For reference, this is the firehol.conf

```

# FireHOL configuration file
#
# See firehol.conf(5) manual page and FireHOL Manual for details.
#
# This configuration file will allow all requests originating from the
# local machine to be send through all network interfaces.
#
# No requests are allowed to come from the network. The host will be
# completely stealthed! It will not respond to anything, and it will
# not be pingable, although it will be able to originate anything
# (even pings to other hosts).
#

version 6

FIREHOL_LOG_MODE = "LOG"
FIREHOL_LOG_LEVEL = "4"

FIREHOL_DROP_ORPHAN_TCP_ACK_FIN=1
FIREHOL_LOG_DROP_INVALID=0

# My SSH thing
server_SSH_ports="tcp/22"
client_SSH_ports="default"

# VPN Server
server_openvpn_ports="tcp/1194"
client_openvpn_ports="default"

# IMAP SSL
server_imapssl_ports="tcp/993"
client_imapssl_ports="default"

# MySQL
server_mysql_ports="tcp/3306"
client_mysql_ports="default"

# Teampspeak
server_teamspeak_ports="udp/8767"
client_teamspeak_ports="default"

# Torrent
server_torrent_ports="udp/51300:51500 tcp/51300:51500"
client_torrent_ports="default"

# voip
server_voip_ports="udp/5060 tcp/5060"
client_voip_ports="default"
server_ts_ports="udp/9987"
client_ts_ports="default"

# block
# block
server_blocker_ports="  tcp/23		udp/23
			tcp/57		udp/67
			tcp/68		udp/68
			tcp/111		udp/111
			tcp/135         udp/135
                        tcp/137         udp/137
                        tcp/138         udp/138
                        tcp/139         udp/139
                        tcp/445         udp/445
                        tcp/1433        udp/1433
                        tcp/1434        udp/1434
                        tcp/2967        udp/2967
                        tcp/5900        udp/5900
                        tcp/6881        udp/6881
                        tcp/3128        udp/3128
                        tcp/59001       udp/59001"
client_blocker_ports="default"

# My Internet Host Ziggo
interface eth4 InetZiggo
	policy drop
	server ident reject with tcp-reset
	
	# I don't know why this doesn't work
	# client multicast reject with proto-unreach

	server SSH		accept
	server http		accept
	server smtp		accept
	server dns		accept
	server openvpn		accept
	server imapssl		accept
	server torrent		accept
	server icmp		accept
	server blocker		reject

	client all			accept
	server all			reject

# Accept all on the Lan
interface eth0 LAN
	client all	accept
	server all	accept

# Accept all on the Bridge
interface br0 Bridge
	client all	accept
	server all	accept

# LXC Bridge	
interface lxcbr0 LXCBridge
	policy accept
	server all		accept
	client all		accept

# LXC Nic
interface veth+ LXCNIC
	policy accept
	server all		accept
	client all		accept

# VPN Tap Device
interface tap0 TapDecvice
	policy accept
	server  all		accept
	client  all		accept	

# Allow routing for the lan
router lan2internet inface eth0 outface eth4
	masquerade
	client all      accept
	server all     accept

# Allow routing for the Bridge
router br2internet inface br0 outface eth4
	masquerade
	client all      accept
	server all      accept

# Allow routing for Bridge To Bridge	
router br2br inface br0 outface br0
	policy accept
	
# Allow all routing for inface lxcbr0
router lx2veth inface lxcbr0 outface veth+
	masquerade
	server all 	accept
	client all	accept

router veth2lx inface veth+ outface lxcbr0
	masquerade
	client all	accept
	server all	accept

```

---

