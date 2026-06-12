---
title: "Dialup Connection Dropping After a Few Minutes"
date: 2005-08-14
forum: Networking &amp; Wireless
---

### Post by Tsuki on 2005-08-14
It's been a while since I was last using Linux on dialup, but I'm sure last time I was (which wouldn't have been on Ubuntu, but still) I didn't have any problems.

Now, though, I'm having a problem whereby I connect fine (using *pon*, set up with *pppconfig*) for a few minutes, then the connection suddenly drops with no warning.  During that time I can use the 'net (*firefox* and *synaptic* are the only programs I've tried using so far), but having to reconnect every few minutes is getting very annoying!

Any ideas as to what might be the problem?  The same connection (Tiscali 56k dialup) with the same hardware (USR External 56k modem) works fine under Windows.

Thanks for any help!

---

### Post by lotusleaf on 2005-08-14
[QUOTE=Tsuki]Any ideas as to what might be the problem?[/QUOTE]

Be sure your *Idle Timeout* is set to **None** in *Advanced Settings* within *pppconfig*. If this doesn't resolve the issue for you, please post again.

---

### Post by Tsuki on 2005-08-15
I'm afraid I've checked that, and the disconnection is still happening...

EDIT:  Okay, I've fiddled with a few more things...  First of all I realised that Windows was authenticating the connection with PAP whereas I had Linux set up to use CHAT.  Even worse - I was actually using the wrong password as well.  Yay, go me.  Still, I'm using PAP with the right password now and still having a similar symptom (although the cause is now something different rather than me not authenticating properly).

From the end of my /var/log/syslog:
```
Aug 15 20:51:24 localhost kernel: CSLIP: code copyright 1989 Regents of the University of California
Aug 15 20:51:25 localhost udev[7380]: creating device node '/dev/ppp'
Aug 15 20:51:25 localhost kernel: PPP generic driver version 2.4.2
Aug 15 20:51:25 localhost pppd[7388]: pppd 2.4.2 started by root, uid 0
Aug 15 20:51:26 localhost chat[7389]: abort on (BUSY)
Aug 15 20:51:26 localhost chat[7389]: abort on (NO CARRIER)
Aug 15 20:51:26 localhost chat[7389]: abort on (VOICE)
Aug 15 20:51:26 localhost chat[7389]: abort on (NO DIALTONE)
Aug 15 20:51:26 localhost chat[7389]: abort on (NO DIAL TONE)
Aug 15 20:51:26 localhost chat[7389]: abort on (NO ANSWER)
Aug 15 20:51:26 localhost chat[7389]: abort on (DELAYED)
Aug 15 20:51:26 localhost chat[7389]: send (ATZ^M)
Aug 15 20:51:26 localhost chat[7389]: expect (OK)
Aug 15 20:51:26 localhost chat[7389]: ATZ^M^M
Aug 15 20:51:26 localhost chat[7389]: OK
Aug 15 20:51:26 localhost chat[7389]:  -- got it 
Aug 15 20:51:26 localhost chat[7389]: send (ATDT147008456614681^M)
Aug 15 20:51:26 localhost chat[7389]: expect (CONNECT)
Aug 15 20:51:26 localhost chat[7389]: ^M
Aug 15 20:51:58 localhost chat[7389]: ATDT147008456614681^M^M
Aug 15 20:51:58 localhost chat[7389]: CONNECT
Aug 15 20:51:58 localhost chat[7389]:  -- got it 
Aug 15 20:51:58 localhost chat[7389]: send (\d)
Aug 15 20:51:59 localhost pppd[7388]: Serial connection established.
Aug 15 20:51:59 localhost pppd[7388]: using channel 1
Aug 15 20:51:59 localhost pppd[7388]: Using interface ppp0
Aug 15 20:51:59 localhost pppd[7388]: Connect: ppp0 <--> /dev/ttyS0
Aug 15 20:52:00 localhost pppd[7388]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xfdaf708> <pcomp> <accomp>]
Aug 15 20:52:00 localhost pppd[7388]: rcvd [LCP ConfReq id=0x96 <asyncmap 0xa0000> <auth pap> <magic 0x2636afbc> <pcomp> <accomp> <mrru 1524> <endpoint [local:43.48.54.53.54.41.43.4b]>]
Aug 15 20:52:00 localhost pppd[7388]: sent [LCP ConfRej id=0x96 <mrru 1524>]
Aug 15 20:52:00 localhost pppd[7388]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xfdaf708> <pcomp> <accomp>]
Aug 15 20:52:00 localhost pppd[7388]: rcvd [LCP ConfReq id=0x97 <asyncmap 0xa0000> <auth pap> <magic 0x2636afbc> <pcomp> <accomp> <endpoint [local:43.48.54.53.54.41.43.4b]>]
Aug 15 20:52:00 localhost pppd[7388]: sent [LCP ConfAck id=0x97 <asyncmap 0xa0000> <auth pap> <magic 0x2636afbc> <pcomp> <accomp> <endpoint [local:43.48.54.53.54.41.43.4b]>]
Aug 15 20:52:00 localhost pppd[7388]: sent [LCP EchoReq id=0x0 magic=0xfdaf708]
Aug 15 20:52:00 localhost pppd[7388]: sent [PAP AuthReq id=0x1 user="andy.renton@tiscali.co.uk" password=<hidden>]
Aug 15 20:52:00 localhost pppd[7388]: rcvd [LCP EchoRep id=0x0 magic=0x2636afbc]
Aug 15 20:52:03 localhost pppd[7388]: sent [PAP AuthReq id=0x2 user="andy.renton@tiscali.co.uk" password=<hidden>]
Aug 15 20:52:06 localhost pppd[7388]: sent [PAP AuthReq id=0x3 user="andy.renton@tiscali.co.uk" password=<hidden>]
Aug 15 20:52:09 localhost pppd[7388]: sent [PAP AuthReq id=0x4 user="andy.renton@tiscali.co.uk" password=<hidden>]
Aug 15 20:52:12 localhost pppd[7388]: sent [PAP AuthReq id=0x5 user="andy.renton@tiscali.co.uk" password=<hidden>]
Aug 15 20:52:15 localhost pppd[7388]: sent [PAP AuthReq id=0x6 user="andy.renton@tiscali.co.uk" password=<hidden>]
Aug 15 20:52:18 localhost pppd[7388]: sent [PAP AuthReq id=0x7 user="andy.renton@tiscali.co.uk" password=<hidden>]
Aug 15 20:52:21 localhost pppd[7388]: sent [PAP AuthReq id=0x8 user="andy.renton@tiscali.co.uk" password=<hidden>]
Aug 15 20:52:23 localhost pppd[7388]: rcvd [PAP AuthAck id=0x8 ""]
Aug 15 20:52:23 localhost pppd[7388]: PAP authentication succeeded
Aug 15 20:52:23 localhost kernel: PPP BSD Compression module registered
Aug 15 20:52:23 localhost pppd[7388]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Aug 15 20:52:23 localhost pppd[7388]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Aug 15 20:52:23 localhost pppd[7388]: rcvd [IPCP ConfReq id=0x1 <addr 212.74.116.4>]
Aug 15 20:52:23 localhost pppd[7388]: sent [IPCP ConfAck id=0x1 <addr 212.74.116.4>]
Aug 15 20:52:23 localhost kernel: PPP Deflate Compression module registered
Aug 15 20:52:23 localhost pppd[7388]: rcvd [LCP ProtRej id=0x1 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Aug 15 20:52:23 localhost pppd[7388]: rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
Aug 15 20:52:23 localhost pppd[7388]: sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Aug 15 20:52:23 localhost pppd[7388]: rcvd [IPCP ConfNak id=0x2 <addr 80.47.64.140> <ms-dns1 80.225.255.185> <ms-dns3 80.225.252.50>]
Aug 15 20:52:23 localhost pppd[7388]: sent [IPCP ConfReq id=0x3 <addr 80.47.64.140> <ms-dns1 80.225.255.185> <ms-dns3 80.225.252.50>]
Aug 15 20:52:23 localhost pppd[7388]: rcvd [IPCP ConfAck id=0x3 <addr 80.47.64.140> <ms-dns1 80.225.255.185> <ms-dns3 80.225.252.50>]
Aug 15 20:52:23 localhost pppd[7388]: Cannot determine ethernet address for proxy ARP
Aug 15 20:52:23 localhost pppd[7388]: local  IP address 80.47.64.140
Aug 15 20:52:23 localhost pppd[7388]: remote IP address 212.74.116.4
Aug 15 20:52:23 localhost pppd[7388]: primary   DNS address 80.225.255.185
Aug 15 20:52:23 localhost pppd[7388]: secondary DNS address 80.225.252.50
Aug 15 20:52:23 localhost pppd[7388]: Script /etc/ppp/ip-up started (pid 7513)
Aug 15 20:52:23 localhost postfix/master[6764]: reload configuration
Aug 15 20:52:23 localhost pppd[7388]: Script /etc/ppp/ip-up finished (pid 7513), status = 0x0
Aug 15 20:52:30 localhost pppd[7388]: rcvd [proto=0xc00a] 01 00 08 26 36 af bc
Aug 15 20:52:30 localhost pppd[7388]: Unsupported protocol 0xc00a received
Aug 15 20:52:30 localhost pppd[7388]: sent [LCP ProtRej id=0x2 c0 0a 01 00 08 26 36 af bc]
Aug 15 20:53:04 localhost pppd[7388]: rcvd [proto=0xc00a] 02 00 08 26 36 af bc
Aug 15 20:53:04 localhost pppd[7388]: Unsupported protocol 0xc00a received
Aug 15 20:53:04 localhost pppd[7388]: sent [LCP ProtRej id=0x3 c0 0a 02 00 08 26 36 af bc]
Aug 15 20:53:38 localhost pppd[7388]: rcvd [proto=0xc00a] 03 00 08 26 36 af bc
Aug 15 20:53:38 localhost pppd[7388]: Unsupported protocol 0xc00a received
Aug 15 20:53:38 localhost pppd[7388]: sent [LCP ProtRej id=0x4 c0 0a 03 00 08 26 36 af bc]
Aug 15 20:54:00 localhost pppd[7388]: rcvd [proto=0xc00a] 04 00 08 26 36 af bc
Aug 15 20:54:00 localhost pppd[7388]: Unsupported protocol 0xc00a received
Aug 15 20:54:00 localhost pppd[7388]: sent [LCP ProtRej id=0x5 c0 0a 04 00 08 26 36 af bc]
Aug 15 20:54:30 localhost pppd[7388]: No response to 4 echo-requests
Aug 15 20:54:30 localhost pppd[7388]: Serial link appears to be disconnected.
Aug 15 20:54:30 localhost pppd[7388]: Connect time 2.2 minutes.
Aug 15 20:54:30 localhost pppd[7388]: Sent 83248 bytes, received 358178 bytes.
Aug 15 20:54:30 localhost pppd[7388]: Script /etc/ppp/ip-down started (pid 7630)
Aug 15 20:54:30 localhost pppd[7388]: sent [LCP TermReq id=0x6 "Peer not responding"]
Aug 15 20:54:30 localhost postfix/master[6764]: reload configuration
Aug 15 20:54:30 localhost pppd[7388]: Script /etc/ppp/ip-down finished (pid 7630), status = 0x0
Aug 15 20:54:31 localhost pppd[7388]: rcvd [LCP TermAck id=0x6]
Aug 15 20:54:31 localhost pppd[7388]: Connection terminated.
Aug 15 20:54:31 localhost pppd[7388]: Hangup (SIGHUP)
Aug 15 20:54:31 localhost pppd[7388]: Exit.
```

Any ideas?  Looks like the hex codes in these pairs of lines match up pretty well:

```
Aug 15 20:54:00 localhost pppd[7388]: rcvd [proto=0xc00a] 04 00 08 26 36 af bc
Aug 15 20:54:00 localhost pppd[7388]: sent [LCP ProtRej id=0x5 c0 0a 04 00 08 26 36 af bc]
```

Is it something like my machine and the host not liking the format of each other's echo requests?  If so, how might I fix this?

Thanks in advance

---

### Post by Tsuki on 2005-08-17
Ah, I've just discovered /etc/ppp/options, which contains the line "lcp-echo-failure 4".  When commented out, the connection stays up properly (although I'm still no closer to finding out why the LCP echoes aren't being responded to).

---

