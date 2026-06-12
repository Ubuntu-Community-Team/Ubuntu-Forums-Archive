---
title: "DUN via Sony Ericsson W900i (Bluetooth)"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by Dark_Neo on 2007-06-18
I've been trying to get DUN working through my W900i (it's on Vodafone), with a fair amount of success (after a lot of attempts). I can get it to connect, and it receives the IP and DNS server, it can lookup IPs, but it can't seem to connect to any.  I think this is because it doesn't find the gateway address, when it's connected I get this output from "ip route":

```
10.64.64.64 dev ppp0  proto kernel  scope link  src 10.184.151.65 
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.4 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default dev ppp0  scope link 
```

Here's the log of the connection:

```
Jun 18 18:02:15 Xianna pppd[14056]: pppd 2.4.4 started by root, uid 0
Jun 18 18:02:19 Xianna hcid[5600]: link_key_request (sba=00:10:60:D1:3F:A3, dba=00:12:EE:D2:EE:D9)
Jun 18 18:02:20 Xianna chat[14061]: abort on (BUSY)
Jun 18 18:02:20 Xianna chat[14061]: abort on (NO CARRIER)
Jun 18 18:02:20 Xianna chat[14061]: abort on (VOICE)
Jun 18 18:02:20 Xianna chat[14061]: abort on (NO DIALTONE)
Jun 18 18:02:20 Xianna chat[14061]: abort on (NO DIAL TONE)
Jun 18 18:02:20 Xianna chat[14061]: abort on (NO ANSWER)
Jun 18 18:02:20 Xianna chat[14061]: abort on (DELAYED)
Jun 18 18:02:20 Xianna chat[14061]: send (ATZ^M)
Jun 18 18:02:20 Xianna chat[14061]: expect (OK)
Jun 18 18:02:20 Xianna chat[14061]: ATZ^M^M
Jun 18 18:02:20 Xianna chat[14061]: OK
Jun 18 18:02:20 Xianna chat[14061]:  -- got it 
Jun 18 18:02:20 Xianna chat[14061]: send (ATDT*99***1#^M)
Jun 18 18:02:20 Xianna chat[14061]: expect (CONNECT)
Jun 18 18:02:20 Xianna chat[14061]: ^M
Jun 18 18:02:21 Xianna chat[14061]: ATDT*99***1#^M^M
Jun 18 18:02:21 Xianna chat[14061]: CONNECT
Jun 18 18:02:21 Xianna chat[14061]:  -- got it 
Jun 18 18:02:21 Xianna chat[14061]: send (\d)
Jun 18 18:02:22 Xianna pppd[14056]: Serial connection established.
Jun 18 18:02:22 Xianna pppd[14056]: using channel 3
Jun 18 18:02:22 Xianna pppd[14056]: Using interface ppp0
Jun 18 18:02:22 Xianna pppd[14056]: Connect: ppp0 <--> /dev/rfcomm0
Jun 18 18:02:23 Xianna pppd[14056]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x34f2682c> <pcomp> <accomp>]
Jun 18 18:02:24 Xianna pppd[14056]: rcvd [LCP ConfReq id=0x2 <auth pap> <accomp> <pcomp> <asyncmap 0x0> <magic 0xa74a7e5>]
Jun 18 18:02:24 Xianna pppd[14056]: sent [LCP ConfAck id=0x2 <auth pap> <accomp> <pcomp> <asyncmap 0x0> <magic 0xa74a7e5>]
Jun 18 18:02:24 Xianna pppd[14056]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x34f2682c> <pcomp> <accomp>]
Jun 18 18:02:24 Xianna pppd[14056]: sent [PAP AuthReq id=0x1 user="wap" password=<hidden>]
Jun 18 18:02:24 Xianna pppd[14056]: rcvd [PAP AuthAck id=0x1 "Congratulations!"]
Jun 18 18:02:24 Xianna pppd[14056]: Remote message: Congratulations!
Jun 18 18:02:24 Xianna pppd[14056]: PAP authentication succeeded
Jun 18 18:02:24 Xianna pppd[14056]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Jun 18 18:02:24 Xianna pppd[14056]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Jun 18 18:02:24 Xianna pppd[14056]: rcvd [LCP ProtRej id=0x1 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Jun 18 18:02:24 Xianna pppd[14056]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Jun 18 18:02:25 Xianna pppd[14056]: rcvd [IPCP ConfReq id=0x1]
Jun 18 18:02:25 Xianna pppd[14056]: sent [IPCP ConfNak id=0x1 <addr 0.0.0.0>]
Jun 18 18:02:25 Xianna pppd[14056]: rcvd [IPCP ConfNak id=0x1 <addr 10.98.253.80> <ms-dns1 10.203.65.68> <ms-dns3 10.203.65.68>]
Jun 18 18:02:25 Xianna pppd[14056]: sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 10.98.253.80> <ms-dns1 10.203.65.68> <ms-dns3 10.203.65.68>]
Jun 18 18:02:25 Xianna pppd[14056]: rcvd [IPCP ConfReq id=0x2]
Jun 18 18:02:25 Xianna pppd[14056]: sent [IPCP ConfAck id=0x2]
Jun 18 18:02:25 Xianna pppd[14056]: rcvd [IPCP ConfAck id=0x2 <compress VJ 0f 01> <addr 10.98.253.80> <ms-dns1 10.203.65.68> <ms-dns3 10.203.65.68>]
Jun 18 18:02:25 Xianna pppd[14056]: Could not determine remote IP address: defaulting to 10.64.64.64
Jun 18 18:02:25 Xianna pppd[14056]: Cannot determine ethernet address for proxy ARP
Jun 18 18:02:25 Xianna pppd[14056]: local  IP address 10.98.253.80
Jun 18 18:02:25 Xianna pppd[14056]: remote IP address 10.64.64.64
Jun 18 18:02:25 Xianna pppd[14056]: primary   DNS address 10.203.65.68
Jun 18 18:02:25 Xianna pppd[14056]: secondary DNS address 10.203.65.68
Jun 18 18:02:25 Xianna pppd[14056]: Script /etc/ppp/ip-up started (pid 14065)
Jun 18 18:02:25 Xianna pppd[14056]: Script /etc/ppp/ip-up finished (pid 14065), status = 0x0
```

As you can see the remote IP address could not be determined...I have no idea why this could be happening...

Here's my peers file:

```
hide-password
noauth
connect "/usr/sbin/chat -v -f /etc/chatscripts/bluetooth-w900"
debug
/dev/rfcomm0
115200
defaultroute
noipdefault
user "wap"
usepeerdns
remotename bluetooth-w900
lcp-echo-interval 0

```

Here's my chatscript file:

```
ABORT BUSY ABORT 'NO CARRIER' ABORT VOICE ABORT 'NO DIALTONE' ABORT 'NO DIAL TONE' ABORT 'NO ANSWER' ABORT DELAYED
# modeminit
'' ATZ
# ispnumber
OK-AT-OK "ATDT*99***1#"
# ispconnect
CONNECT \d\c
# prelogin

# ispname
# isppassword
# postlogin

# end of pppconfig stuff

```


Any ideas?

---

