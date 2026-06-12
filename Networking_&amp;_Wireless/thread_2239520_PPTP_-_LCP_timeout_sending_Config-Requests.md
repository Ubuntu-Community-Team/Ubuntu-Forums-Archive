---
title: "PPTP - LCP: timeout sending Config-Requests"
date: 2014-08-14
forum: Networking &amp; Wireless
---

### Post by nagper on 2014-08-14
Dear all,

I am having problems establishing a pptp connection.

The scenario:

win7 -> winxp(virtualbox(linux(pptpd)))

win7 interface ip: 84.206.118.55

linux interfaceip: 192.168.14.232


tcpdump on the server side:

```
root@techmgmt:/home/nagper# tcpdump -i eth0 proto gretcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
14:15:02.720243 IP 84.206.118.55 > 192.168.14.232: GREv1, call 640, seq 0, length 34: LCP, Conf-Request (0x01), id 0, length 20
14:15:02.742882 IP 192.168.14.232 > 192.168.14.252: GREv1, call 16430, seq 0, length 45: LCP, Conf-Request (0x01), id 1, length 31
14:15:03.970881 IP 84.206.118.55 > 192.168.14.232: GREv1, call 640, seq 1, length 34: LCP, Conf-Request (0x01), id 1, length 20
14:15:05.749064 IP 192.168.14.232 > 192.168.14.252: GREv1, call 16430, seq 1, length 45: LCP, Conf-Request (0x01), id 1, length 31
14:15:06.980507 IP 84.206.118.55 > 192.168.14.232: GREv1, call 640, seq 2, length 34: LCP, Conf-Request (0x01), id 2, length 20
14:15:08.753868 IP 192.168.14.232 > 192.168.14.252: GREv1, call 16430, seq 2, length 45: LCP, Conf-Request (0x01), id 1, length 31

```

pptpd syslog:
```

Aug 14 14:28:19 techmgmt pptpd[2090]: MGR: Launching /usr/sbin/pptpctrl to handle client
Aug 14 14:28:19 techmgmt pptpd[2090]: CTRL: local address = 10.0.0.2
Aug 14 14:28:19 techmgmt pptpd[2090]: CTRL: remote address = 10.0.0.10
Aug 14 14:28:19 techmgmt pptpd[2090]: CTRL: pppd options file = /etc/ppp/pptpd-options
Aug 14 14:28:19 techmgmt pptpd[2090]: CTRL: Client 192.168.14.252 control connection started
Aug 14 14:28:19 techmgmt pptpd[2090]: CTRL: Received PPTP Control Message (type: 1)
Aug 14 14:28:19 techmgmt pptpd[2090]: CTRL: Made a START CTRL CONN RPLY packet
Aug 14 14:28:19 techmgmt pptpd[2090]: CTRL: I wrote 156 bytes to the client.
Aug 14 14:28:19 techmgmt pptpd[2090]: CTRL: Sent packet to client
Aug 14 14:28:19 techmgmt pptpd[2090]: CTRL: Received PPTP Control Message (type: 7)
Aug 14 14:28:19 techmgmt pptpd[2090]: CTRL: Set parameters to 100000000 maxbps, 64 window size
Aug 14 14:28:19 techmgmt pptpd[2090]: CTRL: Made a OUT CALL RPLY packet
Aug 14 14:28:19 techmgmt pptpd[2090]: CTRL: Starting call (launching pppd, opening GRE)
Aug 14 14:28:19 techmgmt pptpd[2090]: CTRL: pty_fd = 6
Aug 14 14:28:19 techmgmt pptpd[2090]: CTRL: tty_fd = 7
Aug 14 14:28:19 techmgmt pptpd[2090]: CTRL: I wrote 32 bytes to the client.
Aug 14 14:28:19 techmgmt pptpd[2090]: CTRL: Sent packet to client
Aug 14 14:28:19 techmgmt pptpd[2091]: CTRL (PPPD Launcher): program binary = /usr/sbin/pppd
Aug 14 14:28:19 techmgmt pptpd[2091]: CTRL (PPPD Launcher): local address = 10.0.0.2
Aug 14 14:28:19 techmgmt pptpd[2091]: CTRL (PPPD Launcher): remote address = 10.0.0.10
Aug 14 14:28:19 techmgmt pptpd[2090]: CTRL: Received PPTP Control Message (type: 15)
Aug 14 14:28:19 techmgmt pptpd[2090]: CTRL: Got a SET LINK INFO packet with standard ACCMs
Aug 14 14:28:19 techmgmt pppd[2091]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Aug 14 14:28:19 techmgmt pppd[2091]: pppd 2.4.5 started by nagper, uid 0
Aug 14 14:28:19 techmgmt pppd[2091]: Using interface ppp0
Aug 14 14:28:19 techmgmt pppd[2091]: Connect: ppp0 <--> /dev/pts/1
**[COLOR=#ff0000]Aug 14 14:28:49 techmgmt pppd[2091]: LCP: timeout sending Config-Requests[/COLOR]**
Aug 14 14:28:49 techmgmt pppd[2091]: Connection terminated.
Aug 14 14:28:49 techmgmt pppd[2091]: Modem hangup
Aug 14 14:28:49 techmgmt pppd[2091]: Exit.
Aug 14 14:28:49 techmgmt pptpd[2090]: GRE: read(fd=6,buffer=b77bd480,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
Aug 14 14:28:49 techmgmt pptpd[2090]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Aug 14 14:28:50 techmgmt pptpd[2090]: CTRL: Reaping child PPP[2091]
Aug 14 14:28:50 techmgmt pptpd[2090]: CTRL: Client 192.168.14.252 control connection finished
Aug 14 14:28:50 techmgmt pptpd[2090]: CTRL: Exiting now
Aug 14 14:28:50 techmgmt pptpd[2030]: MGR: Reaped child 2090

```

The main problem seems to be that pptpd thinks the CLIENT is 192.168.14.252 and sends the GRE package to 192.168.14.252 instead of 84.206.118.55.
Why?


Thanks for any suggestion!

---

### Post by costis on 2015-02-27
For the majority of distributions you must load the nf_conntrack_proto_gre
and nf_conntrack_pptp kernel modules  for certain PPTP/VPN servers. This can be done with:

[code]$ sudo modprobe nf_conntrack_proto_gre nf_conntrack_pptp[\code]

---

