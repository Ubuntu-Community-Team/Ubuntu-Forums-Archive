---
title: "Re: Not all websites are loading- 16.04 LTS"
date: 2016-07-17
forum: Networking &amp; Wireless
---

### Post by danbosse1 on 2016-07-17
[COLOR=#111111][FONT=Ubuntu]I have a problem loading some websites after updating. I am using a Wi-fi connetion and have disabled UFW[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have dns: I ran dig @192.168.0.1 [www.difficult.com](www.difficult.com) and got back positive results.[/FONT][/COLOR]
```
[INDENT]dig @192.168.0.1 www.difficult.com
; <<>> DiG 9.10.3-P4-Ubuntu <<>> @192.168.0.1 www.difficult.com ; (1 server found) ;; global options: +cmd ;; Got answer: ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 4089 ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 4
;; OPT PSEUDOSECTION: ; EDNS: version: 0, flags:; udp: 4096 ;; QUESTION SECTION: ;www.difficult.com. IN A
;; ANSWER SECTION: www.difficult.com. 43200 IN A 66.117.157.35
;; AUTHORITY SECTION:
difficult.com. 172800 IN NS cheese.lanminds.net.
difficult.com. 172800 IN NS ns3.lmi.net.
difficult.com. 172800 IN NS ns2.lmi.net. ;; ADDITIONAL SECTION:
cheese.lanminds.net. 48783 IN A 115.125.246.67
ns3.lmi.net. 48783 IN A 66.117.140.96
ns2.lmi.net. 48783 IN A 66.117.151.5
;; Query time: 121 msec ;; SERVER: 192.168.0.1#53(192.168.0.1) ;; WHEN: Sun Jul 17 02:39:08 EDT 2016 ;; MSG SIZE rcvd: 183
```
[/INDENT][COLOR=#111111][FONT=Ubuntu]
I have run ifconfig -a and the results look good to me[/FONT][/COLOR]
```
[INDENT]wlp6s0 Link encap:Ethernet HWaddr 24:ec:99:5b:0c:d2
inet addr:192.168.0.182 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::792e:948c:29e7:f3d2/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:93912 errors:0 dropped:0 overruns:0 frame:0
TX packets:61358 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:111669895 (111.6 MB) TX bytes:8966689 (8.9 MB)
[/INDENT]
```[COLOR=#111111][FONT=Ubuntu]Results of a site i pinged that I cannot connect to[/FONT][/COLOR]
```
[INDENT]ping www.jobbank.gc.ca PING www.jobbank.gc.ca (167.227.34.131)
56(84) bytes of data. From 192.168.0.182 icmp_seq=1 Destination Port
Unreachable From 192.168.0.182 icmp_seq=2 Destination Port
Unreachable From 192.168.0.182 icmp_seq=3 Destination Port
Unreachable From 192.168.0.182 icmp_seq=4 Destination Port
Unreachable From 192.168.0.182 icmp_seq=5 Destination Port
Unreachable From 192.168.0.182 icmp_seq=6 Destination Port
Unreachable From 192.168.0.182 icmp_seq=7 Destination Port
Unreachable ^C
--- www.jobbank.gc.ca ping statistics --- 7 packets transmitted, 0 received, +7 errors, 100% packet loss, time 6006ms
[/INDENT]
```[COLOR=#111111][FONT=Ubuntu]this is a traceroute of the same site i cannot connect to[/FONT][/COLOR]
```
[INDENT]sudo traceroute 167.227.34.131 traceroute to 167.227.34.131
(167.227.34.131), 30 hops max, 60 byte packets 1 192.168.0.182
(192.168.0.182) 0.231 ms 0.405 ms 0.477 ms
[/INDENT]
```[COLOR=#111111][FONT=Ubuntu]dig @127.0.0.1 (had to re-install dnsmasq) *thanks*[/FONT][/COLOR]
```
[INDENT]; <<>> DiG 9.10.3-P4-Ubuntu <<>> dig @127.0.0.1
;; global options:
+cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 57569
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 1
;; OPT PSEUDOSECTION: ; EDNS: version: 0, flags:; udp: 4096 ;; QUESTION SECTION: ;dig. IN A
;; AUTHORITY SECTION: . 10800 IN SOA a.root-servers.net. nstld.verisign-grs.com. 2016071700 1800 900 604800 86400
;; Query time: 111 msec ;; SERVER: 127.0.0.1#53(127.0.0.1) ;; WHEN: Sun Jul 17 12:28:06 EDT 2016 ;; MSG SIZE rcvd: 107
[/INDENT][COLOR=#111111][FONT=Ubuntu]
```sudo netstat -peanut
```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address Foreign Address State User Inode PID/Program name tcp 0 0 127.0.0.1:53 0.0.0.0:* LISTEN 0 3688388 24742/dnsmasq
tcp 0 0 127.0.1.1:53 0.0.0.0:* LISTEN 0 105524 4237/dnsmasq
tcp 0 0 127.0.0.1:9150 0.0.0.0:* LISTEN 1000 258628 9518/tor
tcp 0 0 127.0.0.1:9151 0.0.0.0:* LISTEN 1000 258629 9518/tor
tcp 0 0 192.168.0.182:57580 172.217.1.110:80 ESTABLISHED 1000 3699194 24859/opera
tcp 0 0 127.0.0.1:9151 127.0.0.1:58176 ESTABLISHED 1000 259205 9518/tor
tcp 0 0 127.0.0.1:9151 127.0.0.1:58180 ESTABLISHED 1000 259209 9518/tor
tcp 0 0 192.168.0.182:49210 172.217.1.99:443 ESTABLISHED 1000 3699144 24859/opera
tcp 0 0 192.168.0.182:33342 107.167.110.245:443 ESTABLISHED 1000 3699149 24859/opera
tcp 0 0 192.168.0.182:55952 107.167.110.247:443 ESTABLISHED 1000 3698969 24859/opera
tcp 0 0 192.168.0.182:52486 91.203.99.18:443 ESTABLISHED 1000 3705507 24859/opera
tcp 0 0 192.168.0.182:52482 91.203.99.18:443 TIME_WAIT 0 0 -
tcp 0 0 127.0.0.1:58186 127.0.0.1:9151 ESTABLISHED 1000 259621 9489/firefox
tcp 0 0 127.0.0.1:58176 127.0.0.1:9151 ESTABLISHED 1000 258632 9489/firefox
tcp 0 0 192.168.0.182:51826 185.21.100.50:9001 ESTABLISHED 1000 259204 9518/tor
tcp 0 0 192.168.0.182:52488 91.203.99.18:443 ESTABLISHED 1000 3705511 24859/opera
tcp 0 0 127.0.0.1:9151 127.0.0.1:58186 ESTABLISHED 1000 259622 9518/tor
tcp 0 0 192.168.0.182:51992 172.217.1.99:80 ESTABLISHED 1000 3698971 24859/opera
tcp 0 0 127.0.0.1:58180 127.0.0.1:9151 ESTABLISHED 1000 258655 9489/firefox
udp 0 0 0.0.0.0:5353 0.0.0.0:* 111 17602 829/avahi-daemon: r udp 0 0 0.0.0.0:43665 0.0.0.0:* 111 17604 829/avahi-daemon: r udp 0 0 127.0.0.1:53 0.0.0.0:* 0 3688387 24742/dnsmasq
udp 0 0 127.0.1.1:53 0.0.0.0:* 0 105523 4237/dnsmasq
udp 0 0 0.0.0.0:68 0.0.0.0:* 0 250152 9105/dhclient
udp 0 0 0.0.0.0:4500 0.0.0.0:* 0 18385 1116/iked
udp 0 0 0.0.0.0:500 0.0.0.0:* 0 18384 1116/iked
udp 0 0 0.0.0.0:631 0.0.0.0:* 0 18597 960/cups-browsed udp6 0 0 :::5353 :::* 111 17603 829/avahi-daemon: r udp6 0 0 :::48810 :::* 111 17605[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
```Any site I can connect to is a normal ping and traceroute response and I can use Tor Browser normally and get to any site[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I can use my cell phone with the same connection and have no problems at all![/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Can anyone shed some light on this situation?[/FONT][/COLOR]

UBUNTU 16.04 LTS - I am not sure how to change my post

---

### Post by QDR06VV9 on 2016-07-17
> **danbosse1 said:**
> UBUNTU 16.04 LTS - I am not sure how to change my post

You do not have quite enough beans yet.:(
If you want give the text you want changed and how you want it to read and I will or can do that for you.

---

### Post by danbosse1 on 2016-07-18
Thanks for the help.  
I did the best I could and the situation got worse.
I did a fresh install and everything is normal again.
It doesn't take long with Mega sync and DropBox.

It did it again!!!!!!
The answer I was looking for is.......
```

sudo ufw disable
sudo iptables -F
sudo ufw enable
```

---

