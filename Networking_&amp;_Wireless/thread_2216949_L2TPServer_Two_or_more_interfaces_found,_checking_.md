---
title: "L2TPServer Two or more interfaces found, checking IP forwarding       	[FAILED]"
date: 2014-04-14
forum: Networking &amp; Wireless
---

### Post by curtis8 on 2014-04-14
Running Ubuntu 13.10

Followed this guide:

[https://help.ubuntu.com/community/L2TPServer](https://help.ubuntu.com/community/L2TPServer)

I HAVE gotten this to work in the past but for some reason I cannot do it this time.

```

root@lubuntu-desktop:~# ipsec verify
Checking your system to see if IPsec got installed and started correctly:
Version check and ipsec on-path                                 [OK]
Linux Openswan U2.6.38/K3.11.0-12-generic (netkey)
Checking for IPsec support in kernel                            [OK]
 SAref kernel support                                           [N/A]
 NETKEY:  Testing XFRM related proc values                      [OK]
    [OK]
    [OK]
Checking that pluto is running                                  [OK]
 Pluto listening for IKE on udp 500                             [OK]
 Pluto listening for NAT-T on udp 4500                          [OK]
Two or more interfaces found, checking IP forwarding            [FAILED]
Checking NAT and MASQUERADEing                                  [OK]
Checking for 'ip' command                                       [OK]
Checking /bin/sh is not /bin/dash                               [OK]
Checking for 'iptables' command                                 [OK]
Opportunistic Encryption Support                                [DISABLED]

```

```

root@lubuntu-desktop:~# tail -f /var/log/auth.log
Apr 15 10:02:19 lubuntu-desktop pluto[2295]: packet from 1.144.190.138:500: received Vendor ID payload [RFC 3947] method set to=115 
Apr 15 10:02:19 lubuntu-desktop pluto[2295]: packet from 1.144.190.138:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike] meth=114, but already using method 115
Apr 15 10:02:19 lubuntu-desktop pluto[2295]: packet from 1.144.190.138:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-08] meth=113, but already using method 115
Apr 15 10:02:19 lubuntu-desktop pluto[2295]: packet from 1.144.190.138:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-07] meth=112, but already using method 115
Apr 15 10:02:19 lubuntu-desktop pluto[2295]: packet from 1.144.190.138:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-06] meth=111, but already using method 115
Apr 15 10:02:19 lubuntu-desktop pluto[2295]: packet from 1.144.190.138:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-05] meth=110, but already using method 115
Apr 15 10:02:19 lubuntu-desktop pluto[2295]: packet from 1.144.190.138:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-04] meth=109, but already using method 115
Apr 15 10:02:19 lubuntu-desktop pluto[2295]: packet from 1.144.190.138:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-03] meth=108, but already using method 115
Apr 15 10:02:19 lubuntu-desktop pluto[2295]: packet from 1.144.190.138:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02] meth=107, but already using method 115
Apr 15 10:02:19 lubuntu-desktop pluto[2295]: packet from 1.144.190.138:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 115
Apr 15 10:02:19 lubuntu-desktop pluto[2295]: packet from 1.144.190.138:500: ignoring Vendor ID payload [FRAGMENTATION 80000000]
Apr 15 10:02:19 lubuntu-desktop pluto[2295]: packet from 1.144.190.138:500: received Vendor ID payload [Dead Peer Detection]
Apr 15 10:02:19 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[5] 1.144.190.138 #5: responding to Main Mode from unknown peer 1.144.190.138
Apr 15 10:02:19 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[5] 1.144.190.138 #5: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Apr 15 10:02:19 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[5] 1.144.190.138 #5: STATE_MAIN_R1: sent MR1, expecting MI2
Apr 15 10:02:19 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[5] 1.144.190.138 #5: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike (MacOS X): both are NATed
Apr 15 10:02:19 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[5] 1.144.190.138 #5: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
Apr 15 10:02:19 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[5] 1.144.190.138 #5: STATE_MAIN_R2: sent MR2, expecting MI3
Apr 15 10:02:20 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[5] 1.144.190.138 #5: ignoring informational payload, type IPSEC_INITIAL_CONTACT msgid=00000000
Apr 15 10:02:20 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[5] 1.144.190.138 #5: Main mode peer ID is ID_IPV4_ADDR: '10.181.38.235'
Apr 15 10:02:20 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[5] 1.144.190.138 #5: switched from "L2TP-PSK-NAT" to "L2TP-PSK-NAT"
Apr 15 10:02:20 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[6] 1.144.190.138 #5: deleting connection "L2TP-PSK-NAT" instance with peer 1.144.190.138 {isakmp=#0/ipsec=#0}
Apr 15 10:02:20 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[6] 1.144.190.138 #5: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
Apr 15 10:02:20 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[6] 1.144.190.138 #5: new NAT mapping for #5, was 1.144.190.138:500, now 1.144.190.138:4500
Apr 15 10:02:20 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[6] 1.144.190.138 #5: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp1024}
Apr 15 10:02:20 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[6] 1.144.190.138 #5: Dead Peer Detection (RFC 3706): enabled
Apr 15 10:02:21 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[6] 1.144.190.138 #5: the peer proposed: 121.218.238.240/32:17/1701 -> 10.181.38.235/32:17/0
Apr 15 10:02:21 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[6] 1.144.190.138 #5: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Apr 15 10:02:21 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[6] 1.144.190.138 #6: responding to Quick Mode proposal {msgid:e300e4d7}
Apr 15 10:02:21 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[6] 1.144.190.138 #6:     us: 10.1.1.11<10.1.1.11>:17/1701
Apr 15 10:02:21 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[6] 1.144.190.138 #6:   them: 1.144.190.138[10.181.38.235]:17/53994===10.181.38.235/32
Apr 15 10:02:21 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[6] 1.144.190.138 #6: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Apr 15 10:02:21 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[6] 1.144.190.138 #6: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Apr 15 10:02:21 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[6] 1.144.190.138 #6: Dead Peer Detection (RFC 3706): enabled
Apr 15 10:02:21 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[6] 1.144.190.138 #6: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Apr 15 10:02:21 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[6] 1.144.190.138 #6: STATE_QUICK_R2: IPsec SA established transport mode {ESP/NAT=>0x0450fb7d <0x00a24de6 xfrm=AES_256-HMAC_SHA1 NATOA=10.181.38.235 NATD=1.144.190.138:4500 DPD=enable}
Apr 15 10:02:41 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[6] 1.144.190.138 #5: received Delete SA(0x0450fb7d) payload: deleting IPSEC State #6
Apr 15 10:02:41 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[6] 1.144.190.138 #5: ERROR: netlink XFRM_MSG_DELPOLICY response for flow eroute_connection delete included errno 2: No such file or directory
Apr 15 10:02:41 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[6] 1.144.190.138 #5: received and ignored informational message
Apr 15 10:02:41 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[6] 1.144.190.138 #5: received Delete SA payload: deleting ISAKMP State #5
Apr 15 10:02:41 lubuntu-desktop pluto[2295]: "L2TP-PSK-NAT"[6] 1.144.190.138: deleting connection "L2TP-PSK-NAT" instance with peer 1.144.190.138 {isakmp=#0/ipsec=#0}
Apr 15 10:02:41 lubuntu-desktop pluto[2295]: packet from 1.144.190.138:4500: received and ignored informational message


```

Sorry for just dumping all this ^ mess for you to look at but I'm pretty sure it's mostly what you would need to help me?

I've double checked all my config files and the only difference to the ones in the guide I mentioned before is my IP addressing.

---

### Post by curtis8 on 2014-04-16
Could someone please help me? It's been a couple days now...

---

### Post by curtis8 on 2014-04-19
Been almost a week now, can someone please just help me?

---

