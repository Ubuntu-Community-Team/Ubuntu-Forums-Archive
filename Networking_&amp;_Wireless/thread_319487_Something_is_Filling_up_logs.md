---
title: "Something is Filling up logs"
date: 2006-12-15
forum: Networking &amp; Wireless
---

### Post by heathaj on 2006-12-15
I need help,

My syslog is be filled up with this noise....
I have no idea what is doing it....


```
Dec 15 16:47:28 heath-desktop last message repeated 2 times
Dec 15 16:47:30 heath-desktop kernel: [17182740.184000] BANDWIDTH_IN:IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:23:79:02:08:00 SRC=10.119.248.1 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=62081 PROTO=UDP SPT=67 DPT=68 LEN=308
Dec 15 16:47:30 heath-desktop last message repeated 2 times
Dec 15 16:47:30 heath-desktop kernel: [17182740.188000] BANDWIDTH_IN:IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:23:79:02:08:00 SRC=10.112.70.1 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=62082 PROTO=UDP SPT=67 DPT=68 LEN=308
Dec 15 16:47:30 heath-desktop last message repeated 2 times
Dec 15 16:47:46 heath-desktop kernel: [17182756.356000] BANDWIDTH_IN:IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:23:79:02:08:00 SRC=10.112.70.1 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=62595 PROTO=UDP SPT=67 DPT=68 LEN=308
Dec 15 16:47:46 heath-desktop last message repeated 2 times
Dec 15 16:47:46 heath-desktop kernel: [17182756.816000] BANDWIDTH_OUT:IN=eth0 OUT=eth1 SRC=192.168.15.101 DST=205.188.7.210 LEN=50 TOS=0x00 PREC=0x00 TTL=127 ID=24991 DF PROTO=TCP SPT=2364 DPT=5190 WINDOW=65329 RES=0x00 ACK PSH URGP=0
Dec 15 16:47:46 heath-desktop kernel: [17182756.876000] BANDWIDTH_IN:IN=eth1 OUT=eth0 SRC=205.188.7.210 DST=192.168.15.101 LEN=40 TOS=0x00 PREC=0x00 TTL=106 ID=25783 DF PROTO=TCP SPT=5190 DPT=2364 WINDOW=16384 RES=0x00 ACK URGP=0

```

I do have shorewall install and it is acting as my router, I think I cut off all logging in shorewall...


Here is my interfaces config

```
#ZONE	INTERFACE	BROADCAST	OPTIONS
net	eth1	detect	dhcp,routefilter,nosmurfs
loc	eth0	detect	tcpflags,nosmurfs,detectnets
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE
```

Here is rules config

```
#ACTION		SOURCE		DEST		PROTO	DEST	SOURCE		ORIGINAL	RATE		USER/
#							PORT	PORT(S)		DEST		LIMIT		GROUP
#								PORT	PORT(S) DEST			LIMIT	GROUP
#
#	Accept DNS connections from the firewall to the network
#
DNS/ACCEPT	$FW	net
#
#	Accept SSH connections from the local network for administration
#
SSH/ACCEPT	loc		$FW
#
#	Allow Ping from the local network
#
Ping/ACCEPT	loc		$FW

#
# Reject Ping from the "bad" net zone.. and prevent your log from being flooded..
#

Ping/REJECT	net		$FW

ACCEPT		$FW		loc		icmp
ACCEPT		$FW		net		icmp
#

VNC/ACCEPT	loc	$FW
FTP/ACCEPT	net	loc:192.168.15.101
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE
```

Here is policy Config

 ```
all	all	DROP	notice
net	all	DROP	notice
net		loc		DROP		info

#
# Policies for traffic originating from the firewall ($FW)
#
# If you want open access to the Internet from your firewall, change the
# $FW to net policy to ACCEPT and remove the 'info' LOG LEVEL.
# This may be useful if you run a proxy server on the firewall.
loc		net		ACCEPT
loc	$FW	ACCEPT
loc	all	REJECT	

#
# Policies for traffic originating from the Internet zone (net)
#
$FW	net	ACCEPT
$FW	loc	ACCEPT
$FW		all		REJECT		

# THE FOLLOWING POLICY MUST BE LAST
net		$FW		DROP		
```


Help..

Thanks
Heath....

---

### Post by heathaj on 2006-12-18
I was able to fix it.... removed iptables and reinstalled shorewall
```

sudo apt-get remove iptables
sudo apt-get install shorewall

```


](*,) :cool:

---

### Post by po0f on 2006-12-18
heathaj,

Logs are automatically rotated and compressed for you.  Unless you have really huge logs (more than a couple dozen megabytes per log file) I wouldn't worry about it.

---

### Post by towsonu2003 on 2006-12-18
I have no idea how you managed to remove [iptables]("http://en.wikipedia.org/wiki/Iptables") and still have a firewall... 

As per your logs:
> **heathaj said:**
> 
```
Dec 15 16:47:28 heath-desktop last message repeated 2 times
Dec 15 16:47:46 heath-desktop kernel: [17182756.876000] BANDWIDTH_IN:IN=eth1 OUT=eth0 SRC=a.b.c.d DST=f.g.h.j LEN=40 TOS=0x00 PREC=0x00 TTL=106 ID=25783 DF PROTO=TCP SPT=5190 DPT=2364 WINDOW=16384 RES=0x00 ACK URGP=0

```


It's not noise. It's telling you that (I believe), it blocked an incoming packet: the tcp packet was coming from a.b.c.d, was generated from port 5190, targeted port 2364. I don't know how to interpret the [FONT="Courier New"]IN=eth1 OUT=eth0[/FONT] as I never used iptables for routing... 

if you didn't tweak log rotating, your logs are compressed, saved for a while, and discarded for you. check the size of the log file by doing ```
 ls -lh /var/log/syslog
``` You can use baobab (apt-get install baobab) to see whether the log directories (or any other part of the machine) are getting too big.

---

### Post by heathaj on 2006-12-18
After about of week.. the log file was 2gigs... 

I think shorewall uses iptables... When i reinstalled Shorewall it installed iptables to....

with a gzip of the log was 400megs...

I'm just glad i can stop pulling my hair out,,,


Heath...

---

### Post by heathaj on 2006-12-18
Well, I give up... I restarted that computer last night not looking at the log file untill just now... see that it just grew to 100megs within 16hours with this junk in it. 

```
Dec 18 19:09:02 heath-desktop kernel: [17256767.656000] BANDWIDTH_OUT:IN=eth0 OUT=eth1 SRC=192.168.15.130 DST=205.188.130.216 LEN=40 TOS=0x00 PREC=0x00 TTL=127 ID=13660 DF PROTO=TCP SPT=1816 DPT=80 WINDOW=17274 RES=0x00 ACK URGP=0
Dec 18 19:09:02 heath-desktop kernel: [17256767.712000] BANDWIDTH_IN:IN=eth1 OUT=eth0 SRC=205.188.130.216 DST=192.168.15.130 LEN=40 TOS=0x00 PREC=0x00 TTL=50 ID=952 DF PROTO=TCP SPT=80 DPT=1816 WINDOW=6589 RES=0x00 ACK URGP=0
Dec 18 19:09:03 heath-desktop kernel: [17256768.532000] BANDWIDTH_IN:IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:01:5c:23:79:02:08:00 SRC=10.112.70.1 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=46563 PROTO=UDP SPT=67 DPT=68 LEN=308
Dec 18 19:09:03 heath-desktop last message repeated 2 times
Dec 18 19:09:07 heath-desktop kernel: [17256772.472000] BANDWIDTH_OUT:IN=eth0 OUT=eth1 SRC=192.168.15.130 DST=205.188.130.216 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=13661 DF PROTO=TCP SPT=1817 DPT=80 WINDOW=16384 RES=0x00 SYN URGP=0
Dec 18 19:09:07 heath-desktop kernel: [17256772.532000] BANDWIDTH_IN:IN=eth1 OUT=eth0 SRC=205.188.130.216 DST=192.168.15.130 LEN=48 TOS=0x00 PREC=0x00 TTL=50 ID=0 DF PROTO=TCP SPT=80 DPT=1817 WINDOW=5840 RES=0x00 ACK SYN URGP=0
Dec 18 19:09:07 heath-desktop kernel: [17256772.616000] BANDWIDTH_OUT:IN=eth0 OUT=eth1 SRC=192.168.15.130 DST=205.188.130.216 LEN=40 TOS=0x00 PREC=0x00 TTL=127 ID=13663 DF PROTO=TCP SPT=1817 DPT=80 WINDOW=17520 RES=0x00 ACK URGP=0
Dec 18 19:09:07 heath-desktop kernel: [17256772.620000] BANDWIDTH_OUT:IN=eth0 OUT=eth1 SRC=192.168.15.130 DST=205.188.130.216 LEN=639 TOS=0x00 PREC=0x00 TTL=127 ID=13664 DF PROTO=TCP SPT=1817 DPT=80 WINDOW=17520 RES=0x00 ACK PSH URGP=0
Dec 18 19:09:07 heath-desktop kernel: [17256772.676000] BANDWIDTH_IN:IN=eth1 OUT=eth0 SRC=205.188.130.216 DST=192.168.15.130 LEN=40 TOS=0x00 PREC=0x00 TTL=50 ID=62483 DF PROTO=TCP SPT=80 DPT=1817 WINDOW=6589 RES=0x00 ACK URGP=0
Dec 18 19:09:07 heath-desktop kernel: [17256772.680000] BANDWIDTH_IN:IN=eth1 OUT=eth0 SRC=205.188.130.216 DST=192.168.15.130 LEN=286 TOS=0x00 PREC=0x00 TTL=50 ID=62484 DF PROTO=TCP SPT=80 DPT=1817 WINDOW=6589 RES=0x00 ACK PSH URGP=0
Dec 18 19:09:07 heath-desktop kernel: [17256772.680000] BANDWIDTH_IN:IN=eth1 OUT=eth0 SRC=205.188.130.216 DST=192.168.15.130 LEN=40 TOS=0x00 PREC=0x00 TTL=50 ID=62485 DF PROTO=TCP SPT=80 DPT=1817 WINDOW=6589 RES=0x00 ACK FIN URGP=0
Dec 18 19:09:07 heath-desktop kernel: [17256772.684000] BANDWIDTH_OUT:IN=eth0 OUT=eth1 SRC=192.168.15.130 DST=205.188.130.216 LEN=40 TOS=0x00 PREC=0x00 TTL=127 ID=13666 DF PROTO=TCP SPT=1817 DPT=80 WINDOW=17274 RES=0x00 ACK FIN URGP=0
Dec 18 19:09:07 heath-desktop kernel: [17256772.684000] BANDWIDTH_OUT:IN=eth0 OUT=eth1 SRC=192.168.15.130 DST=205.188.130.216 LEN=40 TOS=0x00 PREC=0x00 TTL=127 ID=13667 DF PROTO=TCP SPT=1817 DPT=80 WINDOW=17274 RES=0x00 ACK URGP=0
Dec 18 19:09:07 heath-desktop kernel: [17256772.740000] BANDWIDTH_IN:IN=eth1 OUT=eth0 SRC=205.188.130.216 DST=192.168.15.130 LEN=40 TOS=0x00 PREC=0x00 TTL=50 ID=62486 DF PROTO=TCP SPT=80 DPT=1817 WINDOW=6589 RES=0x00 ACK URGP=0
```

:-k :confused: 


Is there anyway to just make it stop?????

---

### Post by scxtt on 2006-12-18
looks like http (80), aol (5190) and udp traffic -- standard stuff ... but it's logging EVERYTHING ... what ports are you forwarding from your router?  you can selectively unforward them and stop the "hits" ...

since you don't seem to have a "traditional" router (right?), it looks like shorewall is just logging most any traffic on eth0 -- you should be able to turn that off, but i don't know how - never used that program - i use kmyfirewall and have entries like this anytime a packet is REJECTED:

[indent]Dec 18 20:42:41 madiera-sabayon [349554.685468] [color=red]KMF[/color]: IN=eth0 OUT= MAC=<my MAC address> SRC=67.149.233.79 DST=192.168.1.100 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=18745 DF PROTO=TCP SPT=3023 [color=red]DPT=5900[/color] WINDOW=64240 RES=0x00 SYN URGP=0[/indent]

KMF is kmyfirewall's way of telling me it's adding the entry ...

so basically some JERK is trying to guess "his" way onto my :0 connection (port 5900) ... it annoys me greatly, but i actually use x11vnc so i have to deal w/ it ... to stop the logging i just unforward port 5900 on my router ...

try and find some reference in shorewall to BANDWIDTH_IN and BANDWIDTH_OUT ...

---

### Post by heathaj on 2006-12-18
Yes, it setup up with two nic's as a router/firewall eth0 is in eth1 is out.... 

I don't have anything FWD out or in... It just logging everthing like you said I've cut off all that I know where to cut off logging in the shorewall config files... I'm to the point to try another firewall, Might try what you said you useing kmyfirewall...


Thanks

---

