---
title: "Not sending/receiving data on 3G USB stick (Ubuntu Server 14.04)"
date: 2014-07-26
forum: Networking &amp; Wireless
---

### Post by ljbade2 on 2014-07-26
I have a newly installed copy of Ubuntu Server 14.04.

I have managed to get it to connect successfully to the Internet via my WiFi (after working around the bugs in the Intel 7260 drivers).

I am now attempting to set up my 3G USB stick which is on a static IP plan. This will be used to access the server from the Internet.

The details:
3G stick: Huawei E1762 branded "Internode"
3G plan: Internode NodeMobile Data with static IP (in Canberra, Australia via the Optus 3G network)

What I have done so far:
Install usb-modeswitch and wvdial.
Edit /etc/wvdial.conf config file:
```
[Dialer Defaults]Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
Phone = *99#
Stupid Mode = 1
Dial Attempts = 0
Password = blah
Username = blah



```
Enable debug and persist on pppd config.
Run sudo wvdial.

wvdial output:
```
leith@server:/etc/ppp$ sudo wvdial--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Jul 26 14:16:21 2014
--> Pid of pppd: 3611
--> pppd: {[7f]
--> Using interface ppp0
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> Authentication (CHAP) started
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> Authentication (CHAP) successful
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> pppd: {[7f]
--> local  IP address 59.167.163.143
--> pppd: {[7f]
--> remote IP address 10.64.64.64
--> pppd: {[7f]
--> primary   DNS address 192.231.203.132
--> pppd: {[7f]
--> secondary DNS address 192.231.203.3
--> pppd: {[7f]
--> pppd: {[7f]
--> Script /etc/ppp/ip-up run successful
--> Default route Ok.
--> Nameserver (DNS) Ok.
--> Connected... Press Ctrl-C to disconnect
--> pppd: {[7f]



```

syslog output from pppd:
```
Jul 26 14:16:21 server pppd[3611]: pppd 2.4.5 started by leith, uid 0Jul 26 14:16:21 server pppd[3611]: using channel 4
Jul 26 14:16:21 server pppd[3611]: Using interface ppp0
Jul 26 14:16:21 server pppd[3611]: Connect: ppp0 <--> /dev/ttyUSB0
Jul 26 14:16:21 server pppd[3611]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x7585b3e6> <pcomp> <accomp>]
Jul 26 14:16:21 server pppd[3611]: rcvd [LCP ConfReq id=0x9 <asyncmap 0x0> <auth chap MD5> <magic 0x11dc7c2> <pcomp> <accomp>]
Jul 26 14:16:21 server pppd[3611]: sent [LCP ConfAck id=0x9 <asyncmap 0x0> <auth chap MD5> <magic 0x11dc7c2> <pcomp> <accomp>]
Jul 26 14:16:21 server pppd[3611]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x7585b3e6> <pcomp> <accomp>]
Jul 26 14:16:21 server pppd[3611]: sent [LCP EchoReq id=0x0 magic=0x7585b3e6]
Jul 26 14:16:21 server pppd[3611]: rcvd [LCP DiscReq id=0xa magic=0x11dc7c2]
Jul 26 14:16:21 server pppd[3611]: rcvd [CHAP Challenge id=0x1 <e023008cee8e335d0edbece308e921d3>, name = "UMTS_CHAP_SRVR"]
Jul 26 14:16:21 server pppd[3611]: sent [CHAP Response id=0x1 <1d4ea873d785fc47bacbdba7e06a87b7>, name = "ljbade"]
Jul 26 14:16:21 server pppd[3611]: rcvd [LCP EchoRep id=0x0 magic=0x11dc7c2 75 85 b3 e6]
Jul 26 14:16:21 server pppd[3611]: rcvd [CHAP Success id=0x1 ""]
Jul 26 14:16:21 server pppd[3611]: CHAP authentication succeeded
Jul 26 14:16:21 server pppd[3611]: CHAP authentication succeeded
Jul 26 14:16:21 server pppd[3611]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Jul 26 14:16:21 server pppd[3611]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Jul 26 14:16:21 server pppd[3611]: rcvd [LCP ProtRej id=0xb 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Jul 26 14:16:21 server pppd[3611]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Jul 26 14:16:22 server pppd[3611]: rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
Jul 26 14:16:22 server pppd[3611]: sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
Jul 26 14:16:23 server pppd[3611]: rcvd [IPCP ConfNak id=0x2 <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
Jul 26 14:16:23 server pppd[3611]: sent [IPCP ConfReq id=0x3 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
Jul 26 14:16:24 server pppd[3611]: rcvd [IPCP ConfNak id=0x3 <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
Jul 26 14:16:24 server pppd[3611]: sent [IPCP ConfReq id=0x4 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
Jul 26 14:16:25 server pppd[3611]: rcvd [IPCP ConfNak id=0x4 <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
Jul 26 14:16:25 server pppd[3611]: sent [IPCP ConfReq id=0x5 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
Jul 26 14:16:26 server pppd[3611]: rcvd [IPCP ConfNak id=0x5 <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
Jul 26 14:16:26 server pppd[3611]: sent [IPCP ConfReq id=0x6 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
Jul 26 14:16:26 server pppd[3611]: rcvd [IPCP ConfReq id=0x6]
Jul 26 14:16:26 server pppd[3611]: sent [IPCP ConfNak id=0x6 <addr 0.0.0.0>]
Jul 26 14:16:26 server pppd[3611]: rcvd [IPCP ConfRej id=0x6 <compress VJ 0f 01> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
Jul 26 14:16:26 server pppd[3611]: sent [IPCP ConfReq id=0x7 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns2 10.11.12.14>]
Jul 26 14:16:26 server pppd[3611]: rcvd [IPCP ConfReq id=0x7]
Jul 26 14:16:26 server pppd[3611]: sent [IPCP ConfAck id=0x7]
Jul 26 14:16:26 server pppd[3611]: rcvd [IPCP ConfNak id=0x7 <addr 59.167.163.143> <ms-dns1 192.231.203.132> <ms-dns2 192.231.203.3>]
Jul 26 14:16:26 server pppd[3611]: sent [IPCP ConfReq id=0x8 <addr 59.167.163.143> <ms-dns1 192.231.203.132> <ms-dns2 192.231.203.3>]
Jul 26 14:16:26 server pppd[3611]: rcvd [IPCP ConfAck id=0x8 <addr 59.167.163.143> <ms-dns1 192.231.203.132> <ms-dns2 192.231.203.3>]
Jul 26 14:16:26 server pppd[3611]: Could not determine remote IP address: defaulting to 10.64.64.64
Jul 26 14:16:26 server pppd[3611]: not replacing existing default route via 192.168.20.1
Jul 26 14:16:26 server pppd[3611]: local  IP address 59.167.163.143
Jul 26 14:16:26 server pppd[3611]: remote IP address 10.64.64.64
Jul 26 14:16:26 server pppd[3611]: primary   DNS address 192.231.203.132
Jul 26 14:16:26 server pppd[3611]: secondary DNS address 192.231.203.3
Jul 26 14:16:26 server pppd[3611]: Script /etc/ppp/ip-up started (pid 3621)
Jul 26 14:16:26 server pppd[3611]: Script /etc/ppp/ip-up finished (pid 3621), status = 0x0



```

After running wvdial I cannot send or receive pings via that interface. The firewall is disabled on the Ubuntu system as well as on the ISP.

Baiscally ping -I ppp0 google.com.au gets 100% lost packets.

Also ping the static IP from another machine also has 100% lost packets.

The only error I can see is this:
Could not determine remote IP address: defaulting to 10.64.64.64

What am I doing wrong?

See attachment for wireless script log (mostly irrelevant output).

---

### Post by ljbade2 on 2014-07-26
After some more Googling it seems you must run:
sudo route add default gw 10.64.64.64

For the connection to work outgoing.

However I still can't ping to the static IP from outside.

But I discovered if I run:
sudo route del default gw 192.168.20.1

It starts working.

But I guess then all traffic will go via 3G instead of WiFi. I only want traffic responding to request from 3G to go back out via 3G.

---

