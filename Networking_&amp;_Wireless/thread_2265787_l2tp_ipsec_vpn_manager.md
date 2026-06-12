---
title: "l2tp ipsec vpn manager"
date: 2015-02-17
forum: Networking &amp; Wireless
---

### Post by alex333 on 2015-02-17
Hi! I'm trying to connect to my l2tp ipsec server using gui tool(l2tp ipsec vpn manager), but i have trouble with it:

syslog:

Feb 18 01:46:59 samsung-laptop L2tpIPsecVpnControlDaemon: Opening client connection
Feb 18 01:46:59 samsung-laptop L2tpIPsecVpnControlDaemon: Opening client connection
Feb 18 01:46:59 samsung-laptop L2tpIPsecVpnControlDaemon: Closing client connection
Feb 18 01:46:59 samsung-laptop L2tpIPsecVpnControlDaemon: Executing command ipsec setup start
Feb 18 01:46:59 samsung-laptop kernel: [14263.929317] NET: Registered protocol family 15
Feb 18 01:46:59 samsung-laptop ipsec_setup: Starting Openswan IPsec U2.6.38/K3.13.0-45-generic...
Feb 18 01:46:59 samsung-laptop ipsec_setup: Using NETKEY(XFRM) stack
Feb 18 01:46:59 samsung-laptop kernel: [14264.103805] Initializing XFRM netlink socket
Feb 18 01:47:00 samsung-laptop kernel: [14264.276310] AVX instructions are not detected.
Feb 18 01:47:00 samsung-laptop kernel: [14264.309543] AVX instructions are not detected.
Feb 18 01:47:00 samsung-laptop kernel: [14264.322429] AVX instructions are not detected.
Feb 18 01:47:00 samsung-laptop kernel: [14264.353301] AVX instructions are not detected.
Feb 18 01:47:00 samsung-laptop kernel: [14264.388840] AVX instructions are not detected.
Feb 18 01:47:00 samsung-laptop kernel: [14264.422118] AVX or AES-NI instructions are not detected.
Feb 18 01:47:00 samsung-laptop kernel: [14264.447205] AVX or AES-NI instructions are not detected.
Feb 18 01:47:00 samsung-laptop ipsec_setup: ...Openswan IPsec started
Feb 18 01:47:00 samsung-laptop L2tpIPsecVpnControlDaemon: Command ipsec setup start finished with exit code 0
Feb 18 01:47:00 samsung-laptop L2tpIPsecVpnControlDaemon: Executing command service xl2tpd start
Feb 18 01:47:00 samsung-laptop pluto: adjusting ipsec.d to /etc/ipsec.d
Feb 18 01:47:00 samsung-laptop ipsec__plutorun: adjusting ipsec.d to /etc/ipsec.d
Feb 18 01:47:00 samsung-laptop xl2tpd[31850]: setsockopt recvref[30]: Protocol not available
Feb 18 01:47:00 samsung-laptop xl2tpd[31850]: This binary does not support kernel L2TP.
Feb 18 01:47:00 samsung-laptop L2tpIPsecVpnControlDaemon: Command service xl2tpd start finished with exit code 0
Feb 18 01:47:00 samsung-laptop xl2tpd[31859]: xl2tpd version xl2tpd-1.3.6 started on samsung-laptop PID:31859
Feb 18 01:47:00 samsung-laptop xl2tpd[31859]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc.
Feb 18 01:47:00 samsung-laptop xl2tpd[31859]: Forked by Scott Balmos and David Stipp, (C) 2001
Feb 18 01:47:00 samsung-laptop xl2tpd[31859]: Inherited by Jeff McAdams, (C) 2002
Feb 18 01:47:00 samsung-laptop xl2tpd[31859]: Forked again by Xelerance ([www.xelerance.com](www.xelerance.com)) (C) 2006
Feb 18 01:47:00 samsung-laptop xl2tpd[31859]: Listening on IP address 0.0.0.0, port 1701
Feb 18 01:47:00 samsung-laptop ipsec__plutorun: 002 added connection description "test"
Feb 18 01:47:00 samsung-laptop L2tpIPsecVpnControlDaemon: Executing command ipsec auto --ready
Feb 18 01:47:00 samsung-laptop L2tpIPsecVpnControlDaemon: Command ipsec auto --ready finished with exit code 0
Feb 18 01:47:00 samsung-laptop L2tpIPsecVpnControlDaemon: Executing command ipsec auto --up test
Feb 18 01:47:00 samsung-laptop L2tpIPsecVpnControlDaemon: Command ipsec auto --up test finished with exit code 0
Feb 18 01:47:01 samsung-laptop xl2tpd[31859]: Connecting to host 46.188.44.37, port 1701
Feb 18 01:47:01 samsung-laptop L2tpIPsecVpnControlDaemon: Closing client connection
Feb 18 01:47:01 samsung-laptop xl2tpd[31859]: Connection established to 46.188.44.37, 1701.  Local: 22232, Remote: 38205 (ref=0/0).
Feb 18 01:47:01 samsung-laptop xl2tpd[31859]: Calling on tunnel 22232
Feb 18 01:47:01 samsung-laptop xl2tpd[31859]: Call established with 46.188.44.37, Local: 9900, Remote: 50687, Serial: 1 (ref=0/0)
Feb 18 01:47:01 samsung-laptop xl2tpd[31859]: start_pppd: I'm running: 
Feb 18 01:47:01 samsung-laptop xl2tpd[31859]: "/usr/sbin/pppd" 
Feb 18 01:47:01 samsung-laptop xl2tpd[31859]: "passive" 
Feb 18 01:47:01 samsung-laptop xl2tpd[31859]: "nodetach" 
Feb 18 01:47:01 samsung-laptop xl2tpd[31859]: ":" 
Feb 18 01:47:01 samsung-laptop xl2tpd[31859]: "file" 
Feb 18 01:47:01 samsung-laptop xl2tpd[31859]: "/etc/ppp/test.options.xl2tpd" 
Feb 18 01:47:01 samsung-laptop xl2tpd[31859]: "/dev/pts/8" 
Feb 18 01:47:01 samsung-laptop pppd[31906]: Plugin passprompt.so loaded.
Feb 18 01:47:01 samsung-laptop pppd[31906]: pppd options in effect:
Feb 18 01:47:01 samsung-laptop pppd[31906]: debug#011#011# (from /etc/ppp/test.options.xl2tpd)
Feb 18 01:47:01 samsung-laptop pppd[31906]: nodetach#011#011# (from command line)
Feb 18 01:47:01 samsung-laptop pppd[31906]: idle 72000#011#011# (from /etc/ppp/test.options.xl2tpd)
Feb 18 01:47:01 samsung-laptop pppd[31906]: ktune#011#011# (from /etc/ppp/test.options.xl2tpd)
Feb 18 01:47:01 samsung-laptop pppd[31906]: dump#011#011# (from /etc/ppp/test.options.xl2tpd)
Feb 18 01:47:01 samsung-laptop pppd[31906]: plugin passprompt.so#011#011# (from /etc/ppp/test.options.xl2tpd)
Feb 18 01:47:01 samsung-laptop pppd[31906]: noauth#011#011# (from /etc/ppp/test.options.xl2tpd)
Feb 18 01:47:01 samsung-laptop pppd[31906]: refuse-eap#011#011# (from /etc/ppp/test.options.xl2tpd)
Feb 18 01:47:01 samsung-laptop pppd[31906]: name tukatsinsky#011#011# (from /etc/ppp/test.options.xl2tpd)
Feb 18 01:47:01 samsung-laptop pppd[31906]: remotename #011#011# (from /etc/ppp/test.options.xl2tpd)
Feb 18 01:47:01 samsung-laptop pppd[31906]: promptprog /usr/bin/L2tpIPsecVpn#011#011# (from /etc/ppp/test.options.xl2tpd)
Feb 18 01:47:01 samsung-laptop pppd[31906]: /dev/pts/8#011#011# (from command line)
Feb 18 01:47:01 samsung-laptop pppd[31906]: lock#011#011# (from /etc/ppp/test.options.xl2tpd)
Feb 18 01:47:01 samsung-laptop pppd[31906]: record /var/log/pppd#011#011# (from /etc/ppp/test.options.xl2tpd)
Feb 18 01:47:01 samsung-laptop pppd[31906]: crtscts#011#011# (from /etc/ppp/test.options.xl2tpd)
Feb 18 01:47:01 samsung-laptop pppd[31906]: modem#011#011# (from /etc/ppp/test.options.xl2tpd)
Feb 18 01:47:01 samsung-laptop pppd[31906]: asyncmap 0#011#011# (from /etc/ppp/test.options.xl2tpd)
Feb 18 01:47:01 samsung-laptop pppd[31906]: passive#011#011# (from command line)
Feb 18 01:47:01 samsung-laptop pppd[31906]: lcp-echo-failure 4#011#011# (from /etc/ppp/options)
Feb 18 01:47:01 samsung-laptop pppd[31906]: lcp-echo-interval 30#011#011# (from /etc/ppp/options)
Feb 18 01:47:01 samsung-laptop pppd[31906]: hide-password#011#011# (from /etc/ppp/test.options.xl2tpd)
Feb 18 01:47:01 samsung-laptop pppd[31906]: ipcp-accept-local#011#011# (from /etc/ppp/test.options.xl2tpd)
Feb 18 01:47:01 samsung-laptop pppd[31906]: ipcp-accept-remote#011#011# (from /etc/ppp/test.options.xl2tpd)
Feb 18 01:47:01 samsung-laptop pppd[31906]: ipparam L2tpIPsecVpn-test#011#011# (from /etc/ppp/test.options.xl2tpd)
Feb 18 01:47:01 samsung-laptop pppd[31906]: noproxyarp#011#011# (from /etc/ppp/test.options.xl2tpd)
Feb 18 01:47:01 samsung-laptop pppd[31906]: :#011#011# (from command line)
Feb 18 01:47:01 samsung-laptop pppd[31906]: noipx#011#011# (from /etc/ppp/test.options.xl2tpd)
Feb 18 01:47:01 samsung-laptop pppd[31906]: pppd 2.4.5 started by root, uid 0
Feb 18 01:47:01 samsung-laptop pppd[31906]: using channel 2414
Feb 18 01:47:01 samsung-laptop pppd[31906]: Using interface ppp0
Feb 18 01:47:01 samsung-laptop pppd[31906]: Connect: ppp0 <--> /dev/pts/11
Feb 18 01:47:01 samsung-laptop pppd[31906]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xd8cebdb0> <pcomp> <accomp>]
Feb 18 01:47:01 samsung-laptop pppd[31906]: rcvd [LCP ConfReq id=0x1 <asyncmap 0x0> <auth chap MD5> <magic 0x57980311> <pcomp> <accomp>]
Feb 18 01:47:01 samsung-laptop pppd[31906]: sent [LCP ConfNak id=0x1 <auth pap>]
Feb 18 01:47:01 samsung-laptop NetworkManager[787]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Feb 18 01:47:01 samsung-laptop NetworkManager[787]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Feb 18 01:47:01 samsung-laptop NetworkManager[787]: <warn> /sys/devices/virtual/net/ppp0: couldn't determine device driver; ignoring...
Feb 18 01:47:01 samsung-laptop pppd[31906]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xd8cebdb0> <pcomp> <accomp>]
Feb 18 01:47:01 samsung-laptop pppd[31906]: rcvd [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0x57980311> <pcomp> <accomp>]
Feb 18 01:47:01 samsung-laptop pppd[31906]: sent [LCP ConfAck id=0x2 <asyncmap 0x0> <magic 0x57980311> <pcomp> <accomp>]
Feb 18 01:47:01 samsung-laptop pppd[31906]: sent [LCP EchoReq id=0x0 magic=0xd8cebdb0]
Feb 18 01:47:01 samsung-laptop pppd[31906]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Feb 18 01:47:01 samsung-laptop pppd[31906]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
Feb 18 01:47:01 samsung-laptop pppd[31906]: rcvd [LCP EchoReq id=0x0 magic=0x57980311]
Feb 18 01:47:01 samsung-laptop pppd[31906]: sent [LCP EchoRep id=0x0 magic=0xd8cebdb0]
Feb 18 01:47:01 samsung-laptop pppd[31906]: rcvd [LCP TermReq id=0x3 "peer refused to authenticate"]
Feb 18 01:47:01 samsung-laptop pppd[31906]: LCP terminated by peer (peer refused to authenticate)
Feb 18 01:47:01 samsung-laptop pppd[31906]: sent [LCP TermAck id=0x3]
Feb 18 01:47:01 samsung-laptop xl2tpd[31859]: control_finish: Connection closed to 46.188.44.37, serial 1 ()
Feb 18 01:47:01 samsung-laptop xl2tpd[31859]: Terminating pppd: sending TERM signal to pid 31906
Feb 18 01:47:01 samsung-laptop pppd[31906]: Terminating on signal 15
Feb 18 01:47:01 samsung-laptop pppd[31906]: Script pppd (charshunt) finished (pid 31907), status = 0x0
Feb 18 01:47:01 samsung-laptop pppd[31906]: Modem hangup
Feb 18 01:47:01 samsung-laptop pppd[31906]: Connection terminated.
Feb 18 01:47:01 samsung-laptop NetworkManager[787]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Feb 18 01:47:01 samsung-laptop pppd[31906]: Exit.




auth.log



Feb 18 01:47:00 samsung-laptop pluto[31839]: "test" #1: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike (MacOS X): both are NATed
Feb 18 01:47:00 samsung-laptop pluto[31839]: "test" #1: transition from state STATE_MAIN_I2 to state STATE_MAIN_I3
Feb 18 01:47:00 samsung-laptop pluto[31839]: "test" #1: STATE_MAIN_I3: sent MI3, expecting MR3
Feb 18 01:47:00 samsung-laptop pluto[31839]: "test" #1: received Vendor ID payload [CAN-IKEv2]
Feb 18 01:47:00 samsung-laptop pluto[31839]: "test" #1: Main mode peer ID is ID_IPV4_ADDR: '46.188.44.37'
Feb 18 01:47:00 samsung-laptop pluto[31839]: "test" #1: transition from state STATE_MAIN_I3 to state STATE_MAIN_I4
Feb 18 01:47:00 samsung-laptop pluto[31839]: "test" #1: STATE_MAIN_I4: ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_128 prf=oakley_sha group=modp2048}
Feb 18 01:47:00 samsung-laptop pluto[31839]: "test" #2: initiating Quick Mode PSK+ENCRYPT+UP+IKEv2ALLOW+SAREFTRACK {using isakmp#1 msgid:6c732765 proposal=defaults pfsgroup=no-pfs}
Feb 18 01:47:00 samsung-laptop pluto[31839]: "test" #2: transition from state STATE_QUICK_I1 to state STATE_QUICK_I2
Feb 18 01:47:00 samsung-laptop pluto[31839]: "test" #2: STATE_QUICK_I2: sent QI2, IPsec SA established transport mode {ESP=>0xc74534ca <0x0be332a9 xfrm=AES_128-HMAC_SHA1 NATOA=none NATD=46.188.44.37:4500 DPD=none}


So, as I understand, ipsec connection established, but problems are in xl2tpd, especially i'm concerned about line "[LCP TermReq id=0x3 "peer refused to authenticate"]".

---

