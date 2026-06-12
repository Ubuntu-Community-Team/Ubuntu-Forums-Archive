---
title: "Openswan L2TP/Ipsec VPN Server Behind ASA NAT for Windows Client Remote Access"
date: 2013-12-18
forum: Networking &amp; Wireless
---

### Post by alessio.dimartino on 2013-12-18
Hi guys,
I cannot successfully login using Windows L2tp client behind cisco 1841 nat into my Openswan natted itself by a cisco asa on public internet.
If I try to connect they on the same subnet or on just routed subnets I've got no issue.
Once I put the Openswan Server behind a Nat I've got this issue. All protocols are allowed on the Cisco Asa for the Openswan server, event the iptables allows any traffic for any chain.
[B]

Linux Openswan U2.6.38/K3.11.0-12-generic (netkey)
Ubuntu 13.10


_In the /var/log/auth.log  I can see the following._[/B]

```

Dec 18 10:37:31 ubuntu pluto[5476]: | *received 384 bytes from 172.16.10.240:500 on eth0 (port=500)
Dec 18 10:37:31 ubuntu pluto[5476]: |  processing version=1.0 packet with exchange type=ISAKMP_XCHG_IDPROT (2)
Dec 18 10:37:31 ubuntu pluto[5476]: packet from 172.16.10.240:500: ignoring Vendor ID payload [MS NT5 ISAKMPOAKLEY 00000008]
Dec 18 10:37:31 ubuntu pluto[5476]: packet from 172.16.10.240:500: received Vendor ID payload [RFC 3947] method set to=115 
Dec 18 10:37:31 ubuntu pluto[5476]: packet from 172.16.10.240:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 115
Dec 18 10:37:31 ubuntu pluto[5476]: packet from 172.16.10.240:500: ignoring Vendor ID payload [FRAGMENTATION]
Dec 18 10:37:31 ubuntu pluto[5476]: packet from 172.16.10.240:500: ignoring Vendor ID payload [MS-Negotiation Discovery Capable]
Dec 18 10:37:31 ubuntu pluto[5476]: packet from 172.16.10.240:500: ignoring Vendor ID payload [Vid-Initial-Contact]
Dec 18 10:37:31 ubuntu pluto[5476]: packet from 172.16.10.240:500: ignoring Vendor ID payload [IKE CGA version 1]
Dec 18 10:37:31 ubuntu pluto[5476]: | instantiating "L2TP-PSK-NAT" for initial Main Mode message received on 172.31.252.12:500
Dec 18 10:37:31 ubuntu pluto[5476]: | instantiated "L2TP-PSK-NAT" for 172.16.10.240
Dec 18 10:37:31 ubuntu pluto[5476]: | creating state object #1 at 0x7f68ed5ce960
Dec 18 10:37:31 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[1] 172.16.10.240
Dec 18 10:37:31 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:31 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:31 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:31 ubuntu pluto[5476]: | inserting state object #1
Dec 18 10:37:31 ubuntu pluto[5476]: | inserting event EVENT_SO_DISCARD, timeout in 0 seconds for #1
Dec 18 10:37:31 ubuntu pluto[5476]: "L2TP-PSK-NAT"[1] 172.16.10.240 #1: responding to Main Mode from unknown peer 172.16.10.240
Dec 18 10:37:31 ubuntu pluto[5476]: "L2TP-PSK-NAT"[1] 172.16.10.240 #1: OAKLEY_GROUP 20 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Dec 18 10:37:31 ubuntu pluto[5476]: "L2TP-PSK-NAT"[1] 172.16.10.240 #1: OAKLEY_GROUP 19 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Dec 18 10:37:31 ubuntu pluto[5476]: | started looking for secret for 172.31.252.12->172.16.10.240 of kind PPK_PSK
Dec 18 10:37:31 ubuntu pluto[5476]: | actually looking for secret for 172.31.252.12->172.16.10.240 of kind PPK_PSK
Dec 18 10:37:31 ubuntu pluto[5476]: | 1: compared key %any to 172.31.252.12 / 172.16.10.240 -> 2
Dec 18 10:37:31 ubuntu pluto[5476]: | 2: compared key 172.31.252.12 to 172.31.252.12 / 172.16.10.240 -> 10
Dec 18 10:37:31 ubuntu pluto[5476]: | line 11: match=10 
Dec 18 10:37:31 ubuntu pluto[5476]: | best_match 0>10 best=0x7f68ed5cb340 (line=11)
Dec 18 10:37:31 ubuntu pluto[5476]: | concluding with best_match=10 best=0x7f68ed5cb340 (lineno=11)
Dec 18 10:37:31 ubuntu pluto[5476]: | complete state transition with STF_OK
Dec 18 10:37:31 ubuntu pluto[5476]: "L2TP-PSK-NAT"[1] 172.16.10.240 #1: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Dec 18 10:37:31 ubuntu pluto[5476]: | sending reply packet to 172.16.10.240:500 (from port 500)
Dec 18 10:37:31 ubuntu pluto[5476]: | sending 144 bytes for STATE_MAIN_R0 through eth0:500 to 172.16.10.240:500 (using #1)
Dec 18 10:37:31 ubuntu pluto[5476]: | inserting event EVENT_RETRANSMIT, timeout in 10 seconds for #1
Dec 18 10:37:31 ubuntu pluto[5476]: "L2TP-PSK-NAT"[1] 172.16.10.240 #1: STATE_MAIN_R1: sent MR1, expecting MI2
Dec 18 10:37:31 ubuntu pluto[5476]: | modecfg pull: noquirk policy: Push not-client
Dec 18 10:37:31 ubuntu pluto[5476]: | phase 1 is done, looking for phase 2 to unpend
Dec 18 10:37:31 ubuntu pluto[5476]: | * processed 0 messages from cryptographic helpers 
Dec 18 10:37:31 ubuntu pluto[5476]: | next event EVENT_RETRANSMIT in 10 seconds for #1
Dec 18 10:37:31 ubuntu pluto[5476]: | next event EVENT_RETRANSMIT in 10 seconds for #1
Dec 18 10:37:32 ubuntu pluto[5476]: |  
Dec 18 10:37:32 ubuntu pluto[5476]: | *received 388 bytes from 172.16.10.240:500 on eth0 (port=500)
Dec 18 10:37:32 ubuntu pluto[5476]: |  processing version=1.0 packet with exchange type=ISAKMP_XCHG_IDPROT (2)
Dec 18 10:37:32 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:32 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:32 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:32 ubuntu pluto[5476]: | v1 peer and cookies match on #1, provided msgid 00000000 vs 00000000
Dec 18 10:37:32 ubuntu pluto[5476]: | v1 state object #1 found, in STATE_MAIN_R1
Dec 18 10:37:32 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[1] 172.16.10.240
Dec 18 10:37:32 ubuntu pluto[5476]: "L2TP-PSK-NAT"[1] 172.16.10.240 #1: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike (MacOS X): both are NATed
Dec 18 10:37:32 ubuntu pluto[5476]: | inserting event EVENT_NAT_T_KEEPALIVE, timeout in 20 seconds
Dec 18 10:37:32 ubuntu pluto[5476]: | helper -1 doing build_kenonce op id: 0
Dec 18 10:37:32 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[1] 172.16.10.240
Dec 18 10:37:32 ubuntu pluto[5476]: | started looking for secret for 172.31.252.12->172.16.10.240 of kind PPK_PSK
Dec 18 10:37:32 ubuntu pluto[5476]: | actually looking for secret for 172.31.252.12->172.16.10.240 of kind PPK_PSK
Dec 18 10:37:32 ubuntu pluto[5476]: | 1: compared key %any to 172.31.252.12 / 172.16.10.240 -> 2
Dec 18 10:37:32 ubuntu pluto[5476]: | 2: compared key 172.31.252.12 to 172.31.252.12 / 172.16.10.240 -> 10
Dec 18 10:37:32 ubuntu pluto[5476]: | line 11: match=10 
Dec 18 10:37:32 ubuntu pluto[5476]: | best_match 0>10 best=0x7f68ed5cb340 (line=11)
Dec 18 10:37:32 ubuntu pluto[5476]: | concluding with best_match=10 best=0x7f68ed5cb340 (lineno=11)
Dec 18 10:37:32 ubuntu pluto[5476]: | parent1 type: 7 group: 14 len: 2752 
Dec 18 10:37:32 ubuntu pluto[5476]: | helper -1 doing compute dh+iv op id: 0
Dec 18 10:37:32 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[1] 172.16.10.240
Dec 18 10:37:32 ubuntu pluto[5476]: | complete state transition with STF_OK
Dec 18 10:37:32 ubuntu pluto[5476]: "L2TP-PSK-NAT"[1] 172.16.10.240 #1: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
Dec 18 10:37:32 ubuntu pluto[5476]: | sending reply packet to 172.16.10.240:500 (from port 500)
Dec 18 10:37:32 ubuntu pluto[5476]: | sending 356 bytes for STATE_MAIN_R1 through eth0:500 to 172.16.10.240:500 (using #1)
Dec 18 10:37:32 ubuntu pluto[5476]: | inserting event EVENT_RETRANSMIT, timeout in 10 seconds for #1
Dec 18 10:37:32 ubuntu pluto[5476]: "L2TP-PSK-NAT"[1] 172.16.10.240 #1: STATE_MAIN_R2: sent MR2, expecting MI3
Dec 18 10:37:32 ubuntu pluto[5476]: | modecfg pull: noquirk policy: push not-client
Dec 18 10:37:32 ubuntu pluto[5476]: | phase 1 is done, looking for phase 2 to unpend
Dec 18 10:37:32 ubuntu pluto[5476]: | complete state transition with STF_INLINE
Dec 18 10:37:32 ubuntu pluto[5476]: | * processed 0 messages from cryptographic helpers 
Dec 18 10:37:32 ubuntu pluto[5476]: | next event EVENT_RETRANSMIT in 10 seconds for #1
Dec 18 10:37:32 ubuntu pluto[5476]: | next event EVENT_RETRANSMIT in 10 seconds for #1
Dec 18 10:37:32 ubuntu pluto[5476]: |  
Dec 18 10:37:32 ubuntu pluto[5476]: | *received 76 bytes from 172.16.10.240:4500 on eth0 (port=4500)
Dec 18 10:37:32 ubuntu pluto[5476]: |  processing version=1.0 packet with exchange type=ISAKMP_XCHG_IDPROT (2)
Dec 18 10:37:32 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:32 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:32 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:32 ubuntu pluto[5476]: | v1 peer and cookies match on #1, provided msgid 00000000 vs 00000000
Dec 18 10:37:32 ubuntu pluto[5476]: | v1 state object #1 found, in STATE_MAIN_R2
Dec 18 10:37:32 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[1] 172.16.10.240
Dec 18 10:37:32 ubuntu pluto[5476]: "L2TP-PSK-NAT"[1] 172.16.10.240 #1: Main mode peer ID is ID_IPV4_ADDR: '192.168.1.10'
Dec 18 10:37:32 ubuntu pluto[5476]: | started looking for secret for 172.31.252.12->172.16.10.240 of kind PPK_PSK
Dec 18 10:37:32 ubuntu pluto[5476]: | actually looking for secret for 172.31.252.12->172.16.10.240 of kind PPK_PSK
Dec 18 10:37:32 ubuntu pluto[5476]: | 1: compared key %any to 172.31.252.12 / 172.16.10.240 -> 2
Dec 18 10:37:32 ubuntu pluto[5476]: | 2: compared key 172.31.252.12 to 172.31.252.12 / 172.16.10.240 -> 10
Dec 18 10:37:32 ubuntu pluto[5476]: | line 11: match=10 
Dec 18 10:37:32 ubuntu pluto[5476]: | best_match 0>10 best=0x7f68ed5cb340 (line=11)
Dec 18 10:37:32 ubuntu pluto[5476]: | concluding with best_match=10 best=0x7f68ed5cb340 (lineno=11)
Dec 18 10:37:32 ubuntu pluto[5476]: | started looking for secret for 172.31.252.12->(none) of kind PPK_PSK
Dec 18 10:37:32 ubuntu pluto[5476]: | replace him to 0.0.0.0
Dec 18 10:37:32 ubuntu pluto[5476]: | actually looking for secret for 172.31.252.12->%any of kind PPK_PSK
Dec 18 10:37:32 ubuntu pluto[5476]: | 1: compared key %any to 172.31.252.12 / %any -> 2
Dec 18 10:37:32 ubuntu pluto[5476]: | 2: compared key 172.31.252.12 to 172.31.252.12 / %any -> 10
Dec 18 10:37:32 ubuntu pluto[5476]: | line 11: match=10 
Dec 18 10:37:32 ubuntu pluto[5476]: | best_match 0>10 best=0x7f68ed5cb340 (line=11)
Dec 18 10:37:32 ubuntu pluto[5476]: | concluding with best_match=10 best=0x7f68ed5cb340 (lineno=11)
Dec 18 10:37:32 ubuntu pluto[5476]: | started looking for secret for 172.31.252.12->(none) of kind PPK_PSK
Dec 18 10:37:32 ubuntu pluto[5476]: | replace him to 0.0.0.0
Dec 18 10:37:32 ubuntu pluto[5476]: | actually looking for secret for 172.31.252.12->%any of kind PPK_PSK
Dec 18 10:37:32 ubuntu pluto[5476]: | 1: compared key %any to 172.31.252.12 / %any -> 2
Dec 18 10:37:32 ubuntu pluto[5476]: | 2: compared key 172.31.252.12 to 172.31.252.12 / %any -> 10
Dec 18 10:37:32 ubuntu pluto[5476]: | line 11: match=10 
Dec 18 10:37:32 ubuntu pluto[5476]: | best_match 0>10 best=0x7f68ed5cb340 (line=11)
Dec 18 10:37:32 ubuntu pluto[5476]: | concluding with best_match=10 best=0x7f68ed5cb340 (lineno=11)
Dec 18 10:37:32 ubuntu pluto[5476]: | offered CA: '%none'
Dec 18 10:37:32 ubuntu pluto[5476]: "L2TP-PSK-NAT"[1] 172.16.10.240 #1: switched from "L2TP-PSK-NAT" to "L2TP-PSK-NAT"
Dec 18 10:37:32 ubuntu pluto[5476]: | instantiated "L2TP-PSK-NAT" for 172.16.10.240
Dec 18 10:37:32 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[1] 172.16.10.240
Dec 18 10:37:32 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: deleting connection "L2TP-PSK-NAT" instance with peer 172.16.10.240 {isakmp=#0/ipsec=#0}
Dec 18 10:37:32 ubuntu pluto[5476]: | thinking about whether to send my certificate:
Dec 18 10:37:32 ubuntu pluto[5476]: |   I have RSA key: OAKLEY_PRESHARED_KEY cert.type: CERT_NONE 
Dec 18 10:37:32 ubuntu pluto[5476]: |   sendcert: CERT_ALWAYSSEND and I did not get a certificate request 
Dec 18 10:37:32 ubuntu pluto[5476]: |   so do not send cert.
Dec 18 10:37:32 ubuntu pluto[5476]: | I did not send a certificate because digital signatures are not being used. (PSK)
Dec 18 10:37:32 ubuntu pluto[5476]: | complete state transition with STF_OK
Dec 18 10:37:32 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
Dec 18 10:37:32 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:32 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: new NAT mapping for #1, was 172.16.10.240:500, now 172.16.10.240:4500
Dec 18 10:37:32 ubuntu pluto[5476]: | sending reply packet to 172.16.10.240:4500 (from port 4500)
Dec 18 10:37:32 ubuntu pluto[5476]: | sending 76 bytes for STATE_MAIN_R2 through eth0:4500 to 172.16.10.240:4500 (using #1)
Dec 18 10:37:32 ubuntu pluto[5476]: | inserting event EVENT_SA_EXPIRE, timeout in 28800 seconds for #1
Dec 18 10:37:32 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp2048}
Dec 18 10:37:32 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:32 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:32 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:32 ubuntu pluto[5476]: | v1 peer and cookies match on #1, provided msgid 00000000 vs 00000000
Dec 18 10:37:32 ubuntu pluto[5476]: | v1 state object #1 found, in STATE_MAIN_R3
Dec 18 10:37:32 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Dec 18 10:37:32 ubuntu pluto[5476]: | modecfg pull: noquirk policy: push not-client
Dec 18 10:37:32 ubuntu pluto[5476]: | phase 1 is done, looking for phase 2 to unpend
Dec 18 10:37:32 ubuntu pluto[5476]: | * processed 0 messages from cryptographic helpers 
Dec 18 10:37:32 ubuntu pluto[5476]: | next event EVENT_NAT_T_KEEPALIVE in 20 seconds
Dec 18 10:37:32 ubuntu pluto[5476]: | next event EVENT_NAT_T_KEEPALIVE in 20 seconds
Dec 18 10:37:32 ubuntu pluto[5476]: |  
Dec 18 10:37:32 ubuntu pluto[5476]: | *received 332 bytes from 172.16.10.240:4500 on eth0 (port=4500)
Dec 18 10:37:32 ubuntu pluto[5476]: |  processing version=1.0 packet with exchange type=ISAKMP_XCHG_QUICK (32)
Dec 18 10:37:32 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:32 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:32 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:32 ubuntu pluto[5476]: | v1 peer and cookies match on #1, provided msgid 00000001 vs 00000000
Dec 18 10:37:32 ubuntu pluto[5476]: | v1 state object not found
Dec 18 10:37:32 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:32 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:32 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:32 ubuntu pluto[5476]: | v1 peer and cookies match on #1, provided msgid 00000000 vs 00000000
Dec 18 10:37:32 ubuntu pluto[5476]: | v1 state object #1 found, in STATE_MAIN_R3
Dec 18 10:37:32 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:32 ubuntu pluto[5476]: | peer client is 192.168.1.10
Dec 18 10:37:32 ubuntu pluto[5476]: | peer client protocol/port is 17/1701
Dec 18 10:37:32 ubuntu pluto[5476]: | our client is 172.16.10.239
Dec 18 10:37:32 ubuntu pluto[5476]: | our client protocol/port is 17/1701
Dec 18 10:37:32 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: the peer proposed: 172.16.10.239/32:17/1701 -> 192.168.1.10/32:17/0
Dec 18 10:37:32 ubuntu pluto[5476]: | using (something - hopefully the IP we or they are NAT'ed to) for transport mode connection "L2TP-PSK-NAT"
Dec 18 10:37:32 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Dec 18 10:37:32 ubuntu pluto[5476]: | duplicating state object #1
Dec 18 10:37:32 ubuntu pluto[5476]: | creating state object #2 at 0x7f68ed5d0270
Dec 18 10:37:32 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:32 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:32 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:32 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:32 ubuntu pluto[5476]: | inserting state object #2
Dec 18 10:37:32 ubuntu pluto[5476]: | inserting event EVENT_SO_DISCARD, timeout in 0 seconds for #2
Dec 18 10:37:32 ubuntu pluto[5476]: | helper -1 doing build_nonce op id: 0
Dec 18 10:37:32 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:32 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #2: responding to Quick Mode proposal {msgid:01000000}
Dec 18 10:37:32 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #2:     us: 172.31.252.12:17/1701---172.31.252.1
Dec 18 10:37:32 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #2:   them: 172.16.10.240[192.168.1.10]:17/1701===192.168.1.10/32
Dec 18 10:37:32 ubuntu pluto[5476]: | route owner of "L2TP-PSK-NAT"[2] 172.16.10.240 unrouted: NULL
Dec 18 10:37:32 ubuntu pluto[5476]: | install_inbound_ipsec_sa() checking if we can route
Dec 18 10:37:32 ubuntu pluto[5476]: | route owner of "L2TP-PSK-NAT"[2] 172.16.10.240 unrouted: NULL; eroute owner: NULL
Dec 18 10:37:32 ubuntu pluto[5476]: | could_route called for L2TP-PSK-NAT (kind=CK_INSTANCE)
Dec 18 10:37:32 ubuntu pluto[5476]: |    routing is easy, or has resolvable near-conflict
Dec 18 10:37:32 ubuntu pluto[5476]: | checking if this is a replacement state
Dec 18 10:37:32 ubuntu pluto[5476]: |   st=0x7f68ed5d0270 ost=(nil) st->serialno=#2 ost->serialno=#0 
Dec 18 10:37:32 ubuntu pluto[5476]: | installing outgoing SA now as refhim=0
Dec 18 10:37:32 ubuntu pluto[5476]: | outgoing SA has refhim=4294901761
Dec 18 10:37:32 ubuntu pluto[5476]: | add inbound eroute 192.168.1.10/32:1701 --17-> 172.31.252.12/32:1701 => tun.10000@172.31.252.12 (raw_eroute)
Dec 18 10:37:32 ubuntu pluto[5476]: | raw_eroute result=1 
Dec 18 10:37:32 ubuntu pluto[5476]: | complete state transition with STF_OK
Dec 18 10:37:32 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #2: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Dec 18 10:37:32 ubuntu pluto[5476]: | sending reply packet to 172.16.10.240:4500 (from port 4500)
Dec 18 10:37:32 ubuntu pluto[5476]: | sending 172 bytes for STATE_QUICK_R0 through eth0:4500 to 172.16.10.240:4500 (using #2)
Dec 18 10:37:32 ubuntu pluto[5476]: | inserting event EVENT_RETRANSMIT, timeout in 10 seconds for #2
Dec 18 10:37:32 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #2: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Dec 18 10:37:32 ubuntu pluto[5476]: | modecfg pull: noquirk policy:push not-client
Dec 18 10:37:32 ubuntu pluto[5476]: | phase 1 is done, looking for phase 2 to unpend
Dec 18 10:37:32 ubuntu pluto[5476]: | complete state transition with STF_INLINE
Dec 18 10:37:32 ubuntu pluto[5476]: | * processed 0 messages from cryptographic helpers 
Dec 18 10:37:32 ubuntu pluto[5476]: | next event EVENT_RETRANSMIT in 10 seconds for #2
Dec 18 10:37:32 ubuntu pluto[5476]: | next event EVENT_RETRANSMIT in 10 seconds for #2
Dec 18 10:37:32 ubuntu pluto[5476]: |  
Dec 18 10:37:32 ubuntu pluto[5476]: | *received 60 bytes from 172.16.10.240:4500 on eth0 (port=4500)
Dec 18 10:37:32 ubuntu pluto[5476]: |  processing version=1.0 packet with exchange type=ISAKMP_XCHG_QUICK (32)
Dec 18 10:37:32 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:32 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:32 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:39 ubuntu pluto[5476]: |  
Dec 18 10:37:39 ubuntu pluto[5476]: | *received 332 bytes from 172.16.10.240:4500 on eth0 (port=4500)
Dec 18 10:37:39 ubuntu pluto[5476]: |  processing version=1.0 packet with exchange type=ISAKMP_XCHG_QUICK (32)
Dec 18 10:37:39 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:39 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:39 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:39 ubuntu pluto[5476]: | v1 peer and cookies match on #4, provided msgid 00000004 vs 00000003
Dec 18 10:37:39 ubuntu pluto[5476]: | v1 peer and cookies match on #1, provided msgid 00000004 vs 00000000
Dec 18 10:37:39 ubuntu pluto[5476]: | v1 state object not found
Dec 18 10:37:39 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:39 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:39 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:39 ubuntu pluto[5476]: | v1 peer and cookies match on #4, provided msgid 00000000 vs 00000003
Dec 18 10:37:39 ubuntu pluto[5476]: | v1 peer and cookies match on #1, provided msgid 00000000 vs 00000000
Dec 18 10:37:39 ubuntu pluto[5476]: | v1 state object #1 found, in STATE_MAIN_R3
Dec 18 10:37:39 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:39 ubuntu pluto[5476]: | peer client is 192.168.1.10
Dec 18 10:37:39 ubuntu pluto[5476]: | peer client protocol/port is 17/1701
Dec 18 10:37:39 ubuntu pluto[5476]: | our client is 172.16.10.239
Dec 18 10:37:39 ubuntu pluto[5476]: | our client protocol/port is 17/1701
Dec 18 10:37:39 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: the peer proposed: 172.16.10.239/32:17/1701 -> 192.168.1.10/32:17/1701
Dec 18 10:37:39 ubuntu pluto[5476]: | using (something - hopefully the IP we or they are NAT'ed to) for transport mode connection "L2TP-PSK-NAT"
Dec 18 10:37:39 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Dec 18 10:37:39 ubuntu pluto[5476]: | duplicating state object #1
Dec 18 10:37:39 ubuntu pluto[5476]: | creating state object #5 at 0x7f68ed5d09e0
Dec 18 10:37:39 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:39 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:39 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:39 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:39 ubuntu pluto[5476]: | inserting state object #5
Dec 18 10:37:39 ubuntu pluto[5476]: | inserting event EVENT_SO_DISCARD, timeout in 0 seconds for #5
Dec 18 10:37:39 ubuntu pluto[5476]: | helper -1 doing build_nonce op id: 0
Dec 18 10:37:39 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:39 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #5: responding to Quick Mode proposal {msgid:04000000}
Dec 18 10:37:39 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #5:     us: 172.31.252.12:17/1701---172.31.252.1
Dec 18 10:37:39 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #5:   them: 172.16.10.240[192.168.1.10]:17/1701===192.168.1.10/32
Dec 18 10:37:39 ubuntu pluto[5476]: | route owner of "L2TP-PSK-NAT"[2] 172.16.10.240 erouted: self
Dec 18 10:37:39 ubuntu pluto[5476]: | install_inbound_ipsec_sa() checking if we can route
Dec 18 10:37:39 ubuntu pluto[5476]: | route owner of "L2TP-PSK-NAT"[2] 172.16.10.240 erouted: self; eroute owner: self
Dec 18 10:37:39 ubuntu pluto[5476]: | could_route called for L2TP-PSK-NAT (kind=CK_INSTANCE)
Dec 18 10:37:39 ubuntu pluto[5476]: |    routing is easy, or has resolvable near-conflict
Dec 18 10:37:39 ubuntu pluto[5476]: | checking if this is a replacement state
Dec 18 10:37:39 ubuntu pluto[5476]: |   st=0x7f68ed5d09e0 ost=0x7f68ed5d0270 st->serialno=#5 ost->serialno=#4 
Dec 18 10:37:39 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #5: keeping refhim=4294901761 during rekey
Dec 18 10:37:39 ubuntu pluto[5476]: | outgoing SA has refhim=4294901761
Dec 18 10:37:39 ubuntu pluto[5476]: | complete state transition with STF_OK
Dec 18 10:37:39 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #5: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Dec 18 10:37:39 ubuntu pluto[5476]: | sending reply packet to 172.16.10.240:4500 (from port 4500)
Dec 18 10:37:39 ubuntu pluto[5476]: | sending 172 bytes for STATE_QUICK_R0 through eth0:4500 to 172.16.10.240:4500 (using #5)
Dec 18 10:37:39 ubuntu pluto[5476]: | inserting event EVENT_RETRANSMIT, timeout in 10 seconds for #5
Dec 18 10:37:39 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #5: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Dec 18 10:37:39 ubuntu pluto[5476]: | modecfg pull: noquirk policy:push not-client
Dec 18 10:37:39 ubuntu pluto[5476]: | phase 1 is done, looking for phase 2 to unpend
Dec 18 10:37:39 ubuntu pluto[5476]: | complete state transition with STF_INLINE
Dec 18 10:37:39 ubuntu pluto[5476]: | * processed 0 messages from cryptographic helpers 
Dec 18 10:37:39 ubuntu pluto[5476]: | next event EVENT_RETRANSMIT in 10 seconds for #5
Dec 18 10:37:39 ubuntu pluto[5476]: | next event EVENT_RETRANSMIT in 10 seconds for #5
Dec 18 10:37:39 ubuntu pluto[5476]: |  
Dec 18 10:37:39 ubuntu pluto[5476]: | *received 60 bytes from 172.16.10.240:4500 on eth0 (port=4500)
Dec 18 10:37:39 ubuntu pluto[5476]: |  processing version=1.0 packet with exchange type=ISAKMP_XCHG_QUICK (32)
Dec 18 10:37:39 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:39 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:39 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:39 ubuntu pluto[5476]: | v1 peer and cookies match on #5, provided msgid 00000004 vs 00000004
Dec 18 10:37:39 ubuntu pluto[5476]: | v1 state object #5 found, in STATE_QUICK_R1
Dec 18 10:37:39 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:39 ubuntu pluto[5476]: | install_ipsec_sa() for #5: outbound only
Dec 18 10:37:39 ubuntu pluto[5476]: | route owner of "L2TP-PSK-NAT"[2] 172.16.10.240 erouted: self; eroute owner: self
Dec 18 10:37:39 ubuntu pluto[5476]: | could_route called for L2TP-PSK-NAT (kind=CK_INSTANCE)
Dec 18 10:37:39 ubuntu pluto[5476]: | sr for #5: erouted
Dec 18 10:37:39 ubuntu pluto[5476]: | route owner of "L2TP-PSK-NAT"[2] 172.16.10.240 erouted: self; eroute owner: self
Dec 18 10:37:39 ubuntu pluto[5476]: | eroute_connection replace eroute 172.31.252.12/32:1701 --17-> 192.168.1.10/32:1701 => esp.a0cc7522@172.16.10.240 (raw_eroute)
Dec 18 10:37:39 ubuntu pluto[5476]: | raw_eroute result=1 
Dec 18 10:37:39 ubuntu pluto[5476]: | route_and_eroute: firewall_notified: true
Dec 18 10:37:39 ubuntu pluto[5476]: | route_and_eroute: instance "L2TP-PSK-NAT"[2] 172.16.10.240, setting eroute_owner {spd=0x7f68ed5cfea0,sr=0x7f68ed5cfea0} to #5 (was #4) (newest_ipsec_sa=#4)
Dec 18 10:37:39 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:39 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:39 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:39 ubuntu pluto[5476]: | v1 peer and cookies match on #5, provided msgid 00000000 vs 00000004
Dec 18 10:37:39 ubuntu pluto[5476]: | v1 peer and cookies match on #4, provided msgid 00000000 vs 00000003
Dec 18 10:37:39 ubuntu pluto[5476]: | v1 peer and cookies match on #1, provided msgid 00000000 vs 00000000
Dec 18 10:37:39 ubuntu pluto[5476]: | v1 state object #1 found, in STATE_MAIN_R3
Dec 18 10:37:39 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #5: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Dec 18 10:37:39 ubuntu pluto[5476]: | complete state transition with STF_OK
Dec 18 10:37:39 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #5: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Dec 18 10:37:39 ubuntu pluto[5476]: | inserting event EVENT_SA_EXPIRE, timeout in 3600 seconds for #5
Dec 18 10:37:39 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #5: STATE_QUICK_R2: IPsec SA established transport mode {ESP/NAT=>0xa0cc7522 <0xb431a2dd xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.10 NATD=172.16.10.240:4500 DPD=none}
Dec 18 10:37:39 ubuntu pluto[5476]: | modecfg pull: noquirk policy:push not-client
Dec 18 10:37:39 ubuntu pluto[5476]: | phase 1 is done, looking for phase 2 to unpend
Dec 18 10:37:39 ubuntu pluto[5476]: | * processed 0 messages from cryptographic helpers 
Dec 18 10:37:39 ubuntu pluto[5476]: | next event EVENT_NAT_T_KEEPALIVE in 13 seconds
Dec 18 10:37:39 ubuntu pluto[5476]: | next event EVENT_NAT_T_KEEPALIVE in 13 seconds
Dec 18 10:37:39 ubuntu pluto[5476]: |  
Dec 18 10:37:39 ubuntu pluto[5476]: | *received 76 bytes from 172.16.10.240:4500 on eth0 (port=4500)
Dec 18 10:37:39 ubuntu pluto[5476]: |  processing version=1.0 packet with exchange type=ISAKMP_XCHG_INFO (5)
Dec 18 10:37:39 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:39 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:39 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:39 ubuntu pluto[5476]: | peer and cookies match on #5, provided msgid 00000000 vs 00000004/00000000
Dec 18 10:37:39 ubuntu pluto[5476]: | peer and cookies match on #4, provided msgid 00000000 vs 00000003/00000000
Dec 18 10:37:39 ubuntu pluto[5476]: | peer and cookies match on #1, provided msgid 00000000 vs 00000000/00000000
Dec 18 10:37:39 ubuntu pluto[5476]: | p15 state object #1 found, in STATE_MAIN_R3
Dec 18 10:37:39 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:39 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:39 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: received Delete SA(0x9876d28f) payload: deleting IPSEC State #4
Dec 18 10:37:39 ubuntu pluto[5476]: | deleting state #4
Dec 18 10:37:39 ubuntu pluto[5476]: | sending 76 bytes for delete notify through eth0:4500 to 172.16.10.240:4500 (using #1)
Dec 18 10:37:39 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: received and ignored informational message
Dec 18 10:37:39 ubuntu pluto[5476]: | complete state transition with STF_IGNORE
Dec 18 10:37:39 ubuntu pluto[5476]: | * processed 0 messages from cryptographic helpers 
Dec 18 10:37:39 ubuntu pluto[5476]: | next event EVENT_NAT_T_KEEPALIVE in 13 seconds
Dec 18 10:37:39 ubuntu pluto[5476]: | next event EVENT_NAT_T_KEEPALIVE in 13 seconds
Dec 18 10:37:47 ubuntu pluto[5476]: |  
Dec 18 10:37:47 ubuntu pluto[5476]: | *received 332 bytes from 172.16.10.240:4500 on eth0 (port=4500)
Dec 18 10:37:47 ubuntu pluto[5476]: |  processing version=1.0 packet with exchange type=ISAKMP_XCHG_QUICK (32)
Dec 18 10:37:47 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:47 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:47 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:47 ubuntu pluto[5476]: | v1 peer and cookies match on #5, provided msgid 00000005 vs 00000004
Dec 18 10:37:47 ubuntu pluto[5476]: | v1 peer and cookies match on #1, provided msgid 00000005 vs 00000000
Dec 18 10:37:47 ubuntu pluto[5476]: | v1 state object not found
Dec 18 10:37:47 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:47 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:47 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:47 ubuntu pluto[5476]: | v1 peer and cookies match on #5, provided msgid 00000000 vs 00000004
Dec 18 10:37:47 ubuntu pluto[5476]: | v1 peer and cookies match on #1, provided msgid 00000000 vs 00000000
Dec 18 10:37:47 ubuntu pluto[5476]: | v1 state object #1 found, in STATE_MAIN_R3
Dec 18 10:37:47 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:47 ubuntu pluto[5476]: | peer client is 192.168.1.10
Dec 18 10:37:47 ubuntu pluto[5476]: | peer client protocol/port is 17/1701
Dec 18 10:37:47 ubuntu pluto[5476]: | our client is 172.16.10.239
Dec 18 10:37:47 ubuntu pluto[5476]: | our client protocol/port is 17/1701
Dec 18 10:37:47 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: the peer proposed: 172.16.10.239/32:17/1701 -> 192.168.1.10/32:17/1701
Dec 18 10:37:47 ubuntu pluto[5476]: | using (something - hopefully the IP we or they are NAT'ed to) for transport mode connection "L2TP-PSK-NAT"
Dec 18 10:37:47 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Dec 18 10:37:47 ubuntu pluto[5476]: | duplicating state object #1
Dec 18 10:37:47 ubuntu pluto[5476]: | creating state object #6 at 0x7f68ed5d0270
Dec 18 10:37:47 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:47 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:47 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:47 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:47 ubuntu pluto[5476]: | inserting state object #6
Dec 18 10:37:47 ubuntu pluto[5476]: | inserting event EVENT_SO_DISCARD, timeout in 0 seconds for #6
Dec 18 10:37:47 ubuntu pluto[5476]: | helper -1 doing build_nonce op id: 0
Dec 18 10:37:47 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:47 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #6: responding to Quick Mode proposal {msgid:05000000}
Dec 18 10:37:47 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #6:     us: 172.31.252.12:17/1701---172.31.252.1
Dec 18 10:37:47 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #6:   them: 172.16.10.240[192.168.1.10]:17/1701===192.168.1.10/32
Dec 18 10:37:47 ubuntu pluto[5476]: | route owner of "L2TP-PSK-NAT"[2] 172.16.10.240 erouted: self
Dec 18 10:37:47 ubuntu pluto[5476]: | install_inbound_ipsec_sa() checking if we can route
Dec 18 10:37:47 ubuntu pluto[5476]: | route owner of "L2TP-PSK-NAT"[2] 172.16.10.240 erouted: self; eroute owner: self
Dec 18 10:37:47 ubuntu pluto[5476]: | could_route called for L2TP-PSK-NAT (kind=CK_INSTANCE)
Dec 18 10:37:47 ubuntu pluto[5476]: |    routing is easy, or has resolvable near-conflict
Dec 18 10:37:47 ubuntu pluto[5476]: | checking if this is a replacement state
Dec 18 10:37:47 ubuntu pluto[5476]: |   st=0x7f68ed5d0270 ost=0x7f68ed5d09e0 st->serialno=#6 ost->serialno=#5 
Dec 18 10:37:47 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #6: keeping refhim=4294901761 during rekey
Dec 18 10:37:47 ubuntu pluto[5476]: | outgoing SA has refhim=4294901761
Dec 18 10:37:47 ubuntu pluto[5476]: | complete state transition with STF_OK
Dec 18 10:37:47 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #6: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Dec 18 10:37:47 ubuntu pluto[5476]: | sending reply packet to 172.16.10.240:4500 (from port 4500)
Dec 18 10:37:47 ubuntu pluto[5476]: | sending 172 bytes for STATE_QUICK_R0 through eth0:4500 to 172.16.10.240:4500 (using #6)
Dec 18 10:37:47 ubuntu pluto[5476]: | inserting event EVENT_RETRANSMIT, timeout in 10 seconds for #6
Dec 18 10:37:47 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #6: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Dec 18 10:37:47 ubuntu pluto[5476]: | modecfg pull: noquirk policy:push not-client
Dec 18 10:37:47 ubuntu pluto[5476]: | phase 1 is done, looking for phase 2 to unpend
Dec 18 10:37:47 ubuntu pluto[5476]: | complete state transition with STF_INLINE
Dec 18 10:37:47 ubuntu pluto[5476]: | * processed 0 messages from cryptographic helpers 
Dec 18 10:37:47 ubuntu pluto[5476]: | next event EVENT_NAT_T_KEEPALIVE in 5 seconds
Dec 18 10:37:47 ubuntu pluto[5476]: | next event EVENT_NAT_T_KEEPALIVE in 5 seconds
Dec 18 10:37:47 ubuntu pluto[5476]: |  
Dec 18 10:37:47 ubuntu pluto[5476]: | *received 60 bytes from 172.16.10.240:4500 on eth0 (port=4500)
Dec 18 10:37:47 ubuntu pluto[5476]: |  processing version=1.0 packet with exchange type=ISAKMP_XCHG_QUICK (32)
Dec 18 10:37:47 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:47 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:47 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:47 ubuntu pluto[5476]: | v1 peer and cookies match on #6, provided msgid 00000005 vs 00000005
Dec 18 10:37:47 ubuntu pluto[5476]: | v1 state object #6 found, in STATE_QUICK_R1
Dec 18 10:37:47 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:47 ubuntu pluto[5476]: | install_ipsec_sa() for #6: outbound only
Dec 18 10:37:47 ubuntu pluto[5476]: | route owner of "L2TP-PSK-NAT"[2] 172.16.10.240 erouted: self; eroute owner: self
Dec 18 10:37:47 ubuntu pluto[5476]: | could_route called for L2TP-PSK-NAT (kind=CK_INSTANCE)
Dec 18 10:37:47 ubuntu pluto[5476]: | sr for #6: erouted
Dec 18 10:37:47 ubuntu pluto[5476]: | route owner of "L2TP-PSK-NAT"[2] 172.16.10.240 erouted: self; eroute owner: self
Dec 18 10:37:47 ubuntu pluto[5476]: | eroute_connection replace eroute 172.31.252.12/32:1701 --17-> 192.168.1.10/32:1701 => esp.3b8f4565@172.16.10.240 (raw_eroute)
Dec 18 10:37:47 ubuntu pluto[5476]: | raw_eroute result=1 
Dec 18 10:37:47 ubuntu pluto[5476]: | route_and_eroute: firewall_notified: true
Dec 18 10:37:47 ubuntu pluto[5476]: | route_and_eroute: instance "L2TP-PSK-NAT"[2] 172.16.10.240, setting eroute_owner {spd=0x7f68ed5cfea0,sr=0x7f68ed5cfea0} to #6 (was #5) (newest_ipsec_sa=#5)
Dec 18 10:37:47 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:47 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:47 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:47 ubuntu pluto[5476]: | v1 peer and cookies match on #6, provided msgid 00000000 vs 00000005
Dec 18 10:37:47 ubuntu pluto[5476]: | v1 peer and cookies match on #5, provided msgid 00000000 vs 00000004
Dec 18 10:37:47 ubuntu pluto[5476]: | v1 peer and cookies match on #1, provided msgid 00000000 vs 00000000
Dec 18 10:37:47 ubuntu pluto[5476]: | v1 state object #1 found, in STATE_MAIN_R3
Dec 18 10:37:47 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #6: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Dec 18 10:37:47 ubuntu pluto[5476]: | complete state transition with STF_OK
Dec 18 10:37:47 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #6: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Dec 18 10:37:47 ubuntu pluto[5476]: | inserting event EVENT_SA_EXPIRE, timeout in 3600 seconds for #6
Dec 18 10:37:47 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #6: STATE_QUICK_R2: IPsec SA established transport mode {ESP/NAT=>0x3b8f4565 <0xe6e7ba8e xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.10 NATD=172.16.10.240:4500 DPD=none}
Dec 18 10:37:47 ubuntu pluto[5476]: | modecfg pull: noquirk policy:push not-client
Dec 18 10:37:47 ubuntu pluto[5476]: | phase 1 is done, looking for phase 2 to unpend
Dec 18 10:37:47 ubuntu pluto[5476]: | * processed 0 messages from cryptographic helpers 
Dec 18 10:37:47 ubuntu pluto[5476]: | next event EVENT_NAT_T_KEEPALIVE in 5 seconds
Dec 18 10:37:47 ubuntu pluto[5476]: | next event EVENT_NAT_T_KEEPALIVE in 5 seconds
Dec 18 10:37:47 ubuntu pluto[5476]: |  
Dec 18 10:37:47 ubuntu pluto[5476]: | *received 76 bytes from 172.16.10.240:4500 on eth0 (port=4500)
Dec 18 10:37:47 ubuntu pluto[5476]: |  processing version=1.0 packet with exchange type=ISAKMP_XCHG_INFO (5)
Dec 18 10:37:47 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:47 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:47 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:47 ubuntu pluto[5476]: | peer and cookies match on #6, provided msgid 00000000 vs 00000005/00000000
Dec 18 10:37:47 ubuntu pluto[5476]: | peer and cookies match on #5, provided msgid 00000000 vs 00000004/00000000
Dec 18 10:37:47 ubuntu pluto[5476]: | peer and cookies match on #1, provided msgid 00000000 vs 00000000/00000000
Dec 18 10:37:47 ubuntu pluto[5476]: | p15 state object #1 found, in STATE_MAIN_R3
Dec 18 10:37:47 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:47 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:47 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: received Delete SA(0xa0cc7522) payload: deleting IPSEC State #5
Dec 18 10:37:47 ubuntu pluto[5476]: | deleting state #5
Dec 18 10:37:47 ubuntu pluto[5476]: | sending 76 bytes for delete notify through eth0:4500 to 172.16.10.240:4500 (using #1)
Dec 18 10:37:47 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: received and ignored informational message
Dec 18 10:37:47 ubuntu pluto[5476]: | complete state transition with STF_IGNORE
Dec 18 10:37:47 ubuntu pluto[5476]: | * processed 0 messages from cryptographic helpers 
Dec 18 10:37:47 ubuntu pluto[5476]: | next event EVENT_NAT_T_KEEPALIVE in 5 seconds
Dec 18 10:37:47 ubuntu pluto[5476]: | next event EVENT_NAT_T_KEEPALIVE in 5 seconds
Dec 18 10:37:52 ubuntu pluto[5476]: |  
Dec 18 10:37:52 ubuntu pluto[5476]: | next event EVENT_NAT_T_KEEPALIVE in 0 seconds
Dec 18 10:37:52 ubuntu pluto[5476]: | *time to handle event
Dec 18 10:37:52 ubuntu pluto[5476]: | handling event EVENT_NAT_T_KEEPALIVE
Dec 18 10:37:52 ubuntu pluto[5476]: | event after this is EVENT_PENDING_PHASE2 in 1 seconds
Dec 18 10:37:52 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:52 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:52 ubuntu pluto[5476]: | sending 1 bytes for NAT-T Keep Alive through eth0:4500 to 172.16.10.240:4500 (using #6)
Dec 18 10:37:52 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:52 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:52 ubuntu pluto[5476]: | sending 1 bytes for NAT-T Keep Alive through eth0:4500 to 172.16.10.240:4500 (using #1)
Dec 18 10:37:52 ubuntu pluto[5476]: | inserting event EVENT_NAT_T_KEEPALIVE, timeout in 20 seconds
Dec 18 10:37:52 ubuntu pluto[5476]: | next event EVENT_PENDING_PHASE2 in 1 seconds
Dec 18 10:37:53 ubuntu pluto[5476]: |  
Dec 18 10:37:53 ubuntu pluto[5476]: | next event EVENT_PENDING_PHASE2 in 0 seconds
Dec 18 10:37:53 ubuntu pluto[5476]: | *time to handle event
Dec 18 10:37:53 ubuntu pluto[5476]: | handling event EVENT_PENDING_PHASE2
Dec 18 10:37:53 ubuntu pluto[5476]: | event after this is EVENT_PENDING_DDNS in 2 seconds
Dec 18 10:37:53 ubuntu pluto[5476]: | inserting event EVENT_PENDING_PHASE2, timeout in 120 seconds
Dec 18 10:37:53 ubuntu pluto[5476]: | pending review: connection "L2TP-PSK-NAT" was not up, skipped
Dec 18 10:37:53 ubuntu pluto[5476]: | pending review: connection "L2TP-PSK-noNAT" was not up, skipped
Dec 18 10:37:53 ubuntu pluto[5476]: | pending review: connection "L2TP-PSK-NAT" was not up, skipped
Dec 18 10:37:53 ubuntu pluto[5476]: | next event EVENT_PENDING_DDNS in 2 seconds
Dec 18 10:37:55 ubuntu pluto[5476]: |  
Dec 18 10:37:55 ubuntu pluto[5476]: | next event EVENT_PENDING_DDNS in 0 seconds
Dec 18 10:37:55 ubuntu pluto[5476]: | *time to handle event
Dec 18 10:37:55 ubuntu pluto[5476]: | handling event EVENT_PENDING_DDNS
Dec 18 10:37:55 ubuntu pluto[5476]: | event after this is EVENT_NAT_T_KEEPALIVE in 17 seconds
Dec 18 10:37:55 ubuntu pluto[5476]: | inserting event EVENT_PENDING_DDNS, timeout in 60 seconds
Dec 18 10:37:55 ubuntu pluto[5476]: | next event EVENT_NAT_T_KEEPALIVE in 17 seconds
Dec 18 10:37:57 ubuntu pluto[5476]: |  
Dec 18 10:37:57 ubuntu pluto[5476]: | *received 332 bytes from 172.16.10.240:4500 on eth0 (port=4500)
Dec 18 10:37:57 ubuntu pluto[5476]: |  processing version=1.0 packet with exchange type=ISAKMP_XCHG_QUICK (32)
Dec 18 10:37:57 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:57 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:57 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:57 ubuntu pluto[5476]: | v1 peer and cookies match on #6, provided msgid 00000006 vs 00000005
Dec 18 10:37:57 ubuntu pluto[5476]: | v1 peer and cookies match on #1, provided msgid 00000006 vs 00000000
Dec 18 10:37:57 ubuntu pluto[5476]: | v1 state object not found
Dec 18 10:37:57 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:57 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:57 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:57 ubuntu pluto[5476]: | v1 peer and cookies match on #6, provided msgid 00000000 vs 00000005
Dec 18 10:37:57 ubuntu pluto[5476]: | v1 peer and cookies match on #1, provided msgid 00000000 vs 00000000
Dec 18 10:37:57 ubuntu pluto[5476]: | v1 state object #1 found, in STATE_MAIN_R3
Dec 18 10:37:57 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:57 ubuntu pluto[5476]: | peer client is 192.168.1.10
Dec 18 10:37:57 ubuntu pluto[5476]: | peer client protocol/port is 17/1701
Dec 18 10:37:57 ubuntu pluto[5476]: | our client is 172.16.10.239
Dec 18 10:37:57 ubuntu pluto[5476]: | our client protocol/port is 17/1701
Dec 18 10:37:57 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: the peer proposed: 172.16.10.239/32:17/1701 -> 192.168.1.10/32:17/1701
Dec 18 10:37:57 ubuntu pluto[5476]: | using (something - hopefully the IP we or they are NAT'ed to) for transport mode connection "L2TP-PSK-NAT"
Dec 18 10:37:57 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Dec 18 10:37:57 ubuntu pluto[5476]: | duplicating state object #1
Dec 18 10:37:57 ubuntu pluto[5476]: | creating state object #7 at 0x7f68ed5d09e0
Dec 18 10:37:57 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:57 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:57 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:57 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:57 ubuntu pluto[5476]: | inserting state object #7
Dec 18 10:37:57 ubuntu pluto[5476]: | inserting event EVENT_SO_DISCARD, timeout in 0 seconds for #7
Dec 18 10:37:57 ubuntu pluto[5476]: | helper -1 doing build_nonce op id: 0
Dec 18 10:37:57 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:57 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #7: responding to Quick Mode proposal {msgid:06000000}
Dec 18 10:37:57 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #7:     us: 172.31.252.12:17/1701---172.31.252.1
Dec 18 10:37:57 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #7:   them: 172.16.10.240[192.168.1.10]:17/1701===192.168.1.10/32
Dec 18 10:37:57 ubuntu pluto[5476]: | route owner of "L2TP-PSK-NAT"[2] 172.16.10.240 erouted: self
Dec 18 10:37:57 ubuntu pluto[5476]: | install_inbound_ipsec_sa() checking if we can route
Dec 18 10:37:57 ubuntu pluto[5476]: | route owner of "L2TP-PSK-NAT"[2] 172.16.10.240 erouted: self; eroute owner: self
Dec 18 10:37:57 ubuntu pluto[5476]: | could_route called for L2TP-PSK-NAT (kind=CK_INSTANCE)
Dec 18 10:37:57 ubuntu pluto[5476]: |    routing is easy, or has resolvable near-conflict
Dec 18 10:37:57 ubuntu pluto[5476]: | checking if this is a replacement state
Dec 18 10:37:57 ubuntu pluto[5476]: |   st=0x7f68ed5d09e0 ost=0x7f68ed5d0270 st->serialno=#7 ost->serialno=#6 
Dec 18 10:37:57 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #7: keeping refhim=4294901761 during rekey
Dec 18 10:37:57 ubuntu pluto[5476]: | outgoing SA has refhim=4294901761
Dec 18 10:37:57 ubuntu pluto[5476]: | complete state transition with STF_OK
Dec 18 10:37:57 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #7: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Dec 18 10:37:57 ubuntu pluto[5476]: | sending reply packet to 172.16.10.240:4500 (from port 4500)
Dec 18 10:37:57 ubuntu pluto[5476]: | sending 172 bytes for STATE_QUICK_R0 through eth0:4500 to 172.16.10.240:4500 (using #7)
Dec 18 10:37:57 ubuntu pluto[5476]: | inserting event EVENT_RETRANSMIT, timeout in 10 seconds for #7
Dec 18 10:37:57 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #7: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Dec 18 10:37:57 ubuntu pluto[5476]: | modecfg pull: noquirk policy:push not-client
Dec 18 10:37:57 ubuntu pluto[5476]: | phase 1 is done, looking for phase 2 to unpend
Dec 18 10:37:57 ubuntu pluto[5476]: | complete state transition with STF_INLINE
Dec 18 10:37:57 ubuntu pluto[5476]: | * processed 0 messages from cryptographic helpers 
Dec 18 10:37:57 ubuntu pluto[5476]: | next event EVENT_RETRANSMIT in 10 seconds for #7
Dec 18 10:37:57 ubuntu pluto[5476]: | next event EVENT_RETRANSMIT in 10 seconds for #7
Dec 18 10:37:57 ubuntu pluto[5476]: |  
Dec 18 10:37:57 ubuntu pluto[5476]: | *received 60 bytes from 172.16.10.240:4500 on eth0 (port=4500)
Dec 18 10:37:57 ubuntu pluto[5476]: |  processing version=1.0 packet with exchange type=ISAKMP_XCHG_QUICK (32)
Dec 18 10:37:57 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:57 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:57 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:57 ubuntu pluto[5476]: | v1 peer and cookies match on #7, provided msgid 00000006 vs 00000006
Dec 18 10:37:57 ubuntu pluto[5476]: | v1 state object #7 found, in STATE_QUICK_R1
Dec 18 10:37:57 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:57 ubuntu pluto[5476]: | install_ipsec_sa() for #7: outbound only
Dec 18 10:37:57 ubuntu pluto[5476]: | route owner of "L2TP-PSK-NAT"[2] 172.16.10.240 erouted: self; eroute owner: self
Dec 18 10:37:57 ubuntu pluto[5476]: | could_route called for L2TP-PSK-NAT (kind=CK_INSTANCE)
Dec 18 10:37:57 ubuntu pluto[5476]: | sr for #7: erouted
Dec 18 10:37:57 ubuntu pluto[5476]: | route owner of "L2TP-PSK-NAT"[2] 172.16.10.240 erouted: self; eroute owner: self
Dec 18 10:37:57 ubuntu pluto[5476]: | eroute_connection replace eroute 172.31.252.12/32:1701 --17-> 192.168.1.10/32:1701 => esp.f97df784@172.16.10.240 (raw_eroute)
Dec 18 10:37:57 ubuntu pluto[5476]: | raw_eroute result=1 
Dec 18 10:37:57 ubuntu pluto[5476]: | route_and_eroute: firewall_notified: true
Dec 18 10:37:57 ubuntu pluto[5476]: | route_and_eroute: instance "L2TP-PSK-NAT"[2] 172.16.10.240, setting eroute_owner {spd=0x7f68ed5cfea0,sr=0x7f68ed5cfea0} to #7 (was #6) (newest_ipsec_sa=#6)
Dec 18 10:37:57 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:57 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:57 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:57 ubuntu pluto[5476]: | v1 peer and cookies match on #7, provided msgid 00000000 vs 00000006
Dec 18 10:37:57 ubuntu pluto[5476]: | v1 peer and cookies match on #6, provided msgid 00000000 vs 00000005
Dec 18 10:37:57 ubuntu pluto[5476]: | v1 peer and cookies match on #1, provided msgid 00000000 vs 00000000
Dec 18 10:37:57 ubuntu pluto[5476]: | v1 state object #1 found, in STATE_MAIN_R3
Dec 18 10:37:57 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #7: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Dec 18 10:37:57 ubuntu pluto[5476]: | complete state transition with STF_OK
Dec 18 10:37:57 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #7: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Dec 18 10:37:57 ubuntu pluto[5476]: | inserting event EVENT_SA_EXPIRE, timeout in 3600 seconds for #7
Dec 18 10:37:57 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #7: STATE_QUICK_R2: IPsec SA established transport mode {ESP/NAT=>0xf97df784 <0x3fa1f827 xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.10 NATD=172.16.10.240:4500 DPD=none}
Dec 18 10:37:57 ubuntu pluto[5476]: | modecfg pull: noquirk policy:push not-client
Dec 18 10:37:57 ubuntu pluto[5476]: | phase 1 is done, looking for phase 2 to unpend
Dec 18 10:37:57 ubuntu pluto[5476]: | * processed 0 messages from cryptographic helpers 
Dec 18 10:37:57 ubuntu pluto[5476]: | next event EVENT_NAT_T_KEEPALIVE in 15 seconds
Dec 18 10:37:57 ubuntu pluto[5476]: | next event EVENT_NAT_T_KEEPALIVE in 15 seconds
Dec 18 10:37:57 ubuntu pluto[5476]: |  
Dec 18 10:37:57 ubuntu pluto[5476]: | *received 76 bytes from 172.16.10.240:4500 on eth0 (port=4500)
Dec 18 10:37:57 ubuntu pluto[5476]: |  processing version=1.0 packet with exchange type=ISAKMP_XCHG_INFO (5)
Dec 18 10:37:57 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:37:57 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:37:57 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:37:57 ubuntu pluto[5476]: | peer and cookies match on #7, provided msgid 00000000 vs 00000006/00000000
Dec 18 10:37:57 ubuntu pluto[5476]: | peer and cookies match on #6, provided msgid 00000000 vs 00000005/00000000
Dec 18 10:37:57 ubuntu pluto[5476]: | peer and cookies match on #1, provided msgid 00000000 vs 00000000/00000000
Dec 18 10:37:57 ubuntu pluto[5476]: | p15 state object #1 found, in STATE_MAIN_R3
Dec 18 10:37:57 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:57 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:37:57 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: received Delete SA(0x3b8f4565) payload: deleting IPSEC State #6
Dec 18 10:37:57 ubuntu pluto[5476]: | deleting state #6
Dec 18 10:37:57 ubuntu pluto[5476]: | sending 76 bytes for delete notify through eth0:4500 to 172.16.10.240:4500 (using #1)
Dec 18 10:37:57 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: received and ignored informational message
Dec 18 10:37:57 ubuntu pluto[5476]: | complete state transition with STF_IGNORE
Dec 18 10:37:57 ubuntu pluto[5476]: | * processed 0 messages from cryptographic helpers 
Dec 18 10:37:57 ubuntu pluto[5476]: | next event EVENT_NAT_T_KEEPALIVE in 15 seconds
Dec 18 10:37:57 ubuntu pluto[5476]: | next event EVENT_NAT_T_KEEPALIVE in 15 seconds
Dec 18 10:38:07 ubuntu pluto[5476]: |  
Dec 18 10:38:07 ubuntu pluto[5476]: | *received 76 bytes from 172.16.10.240:4500 on eth0 (port=4500)
Dec 18 10:38:07 ubuntu pluto[5476]: |  processing version=1.0 packet with exchange type=ISAKMP_XCHG_INFO (5)
Dec 18 10:38:07 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:38:07 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:38:07 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:38:07 ubuntu pluto[5476]: | peer and cookies match on #7, provided msgid 00000000 vs 00000006/00000000
Dec 18 10:38:07 ubuntu pluto[5476]: | peer and cookies match on #1, provided msgid 00000000 vs 00000000/00000000
Dec 18 10:38:07 ubuntu pluto[5476]: | p15 state object #1 found, in STATE_MAIN_R3
Dec 18 10:38:07 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:38:07 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:38:07 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: received Delete SA(0xf97df784) payload: deleting IPSEC State #7
Dec 18 10:38:07 ubuntu pluto[5476]: | deleting state #7
Dec 18 10:38:07 ubuntu pluto[5476]: | sending 76 bytes for delete notify through eth0:4500 to 172.16.10.240:4500 (using #1)
Dec 18 10:38:07 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:38:07 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:38:07 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:38:07 ubuntu pluto[5476]: | command executing down-host
Dec 18 10:38:07 ubuntu pluto[5476]: | executing down-host: 2>&1 PLUTO_VERB='down-host' PLUTO_VERSION='2.0' PLUTO_CONNECTION='L2TP-PSK-NAT' PLUTO_INTERFACE='eth0' PLUTO_NEXT_HOP='172.31.252.1' PLUTO_ME='172.31.252.12' PLUTO_MY_ID='172.31.252.12' PLUTO_MY_CLIENT='172.31.252.12/32' PLUTO_MY_CLIENT_NET='172.31.252.12' PLUTO_MY_CLIENT_MASK='255.255.255.255' PLUTO_MY_PORT='1701' PLUTO_MY_PROTOCOL='17' PLUTO_PEER='172.16.10.240' PLUTO_PEER_ID='192.168.1.10' PLUTO_PEER_CLIENT='192.168.1.10/32' PLUTO_PEER_CLIENT_NET='192.168.1.10' PLUTO_PEER_CLIENT_MASK='255.255.255.255' PLUTO_PEER_PORT='1701' PLUTO_PEER_PROTOCOL='17' PLUTO_PEER_CA='' PLUTO_STACK='netkey'   PLUTO_CONN_POLICY='PSK+ENCRYPT+DONTREKEY+IKEv2ALLOW+SAREFTRACK' PLUTO_CONN_ADDRFAMILY='ipv4' PLUTO_XAUTH_USERNAME=''  PLUTO_IS_PEER_CISCO='0' PLUTO_CISCO_DNS_INFO='' PLUTO_CISCO_DOMAIN_INFO='' PLUTO_PEER_BANNER='' PLUTO_NM_CONFIGURED='0' ipsec _updown
Dec 18 10:38:07 ubuntu pluto[5476]: | popen(): cmd is 849 chars long
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd(   0):2>&1 PLUTO_VERB='down-host' PLUTO_VERSION='2.0' PLUTO_CONNECTION='L2TP-PSK-NAT' :
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd(  80)PLUTO_INTERFACE='eth0' PLUTO_NEXT_HOP='172.31.252.1' PLUTO_ME='172.31.252.12' PL:
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd( 160):UTO_MY_ID='172.31.252.12' PLUTO_MY_CLIENT='172.31.252.12/32' PLUTO_MY_CLIENT_NET:
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd( 240):='172.31.252.12' PLUTO_MY_CLIENT_MASK='255.255.255.255' PLUTO_MY_PORT='1701' PLU:
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd( 320):TO_MY_PROTOCOL='17' PLUTO_PEER='172.16.10.240' PLUTO_PEER_ID='192.168.1.10' PLUT:
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd( 400):O_PEER_CLIENT='192.168.1.10/32' PLUTO_PEER_CLIENT_NET='192.168.1.10' PLUTO_PEER_:
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd( 480):CLIENT_MASK='255.255.255.255' PLUTO_PEER_PORT='1701' PLUTO_PEER_PROTOCOL='17' PL:
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd( 560):UTO_PEER_CA='' PLUTO_STACK='netkey'   PLUTO_CONN_POLICY='PSK+ENCRYPT+DONTREKEY+I:
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd( 640):KEv2ALLOW+SAREFTRACK' PLUTO_CONN_ADDRFAMILY='ipv4' PLUTO_XAUTH_USERNAME=''  PLUT:
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd( 720):O_IS_PEER_CISCO='0' PLUTO_CISCO_DNS_INFO='' PLUTO_CISCO_DOMAIN_INFO='' PLUTO_PEE:
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd( 800):R_BANNER='' PLUTO_NM_CONFIGURED='0' ipsec _updown:
Dec 18 10:38:07 ubuntu pluto[5476]: | request to delete a unrouted policy with netkey kernel --- experimental
Dec 18 10:38:07 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: ERROR: netlink XFRM_MSG_DELPOLICY response for flow eroute_connection delete included errno 2: No such file or directory
Dec 18 10:38:07 ubuntu pluto[5476]: | route owner of "L2TP-PSK-NAT"[2] 172.16.10.240 unrouted: NULL
Dec 18 10:38:07 ubuntu pluto[5476]: | command executing unroute-host
Dec 18 10:38:07 ubuntu pluto[5476]: | executing unroute-host: 2>&1 PLUTO_VERB='unroute-host' PLUTO_VERSION='2.0' PLUTO_CONNECTION='L2TP-PSK-NAT' PLUTO_INTERFACE='eth0' PLUTO_NEXT_HOP='172.31.252.1' PLUTO_ME='172.31.252.12' PLUTO_MY_ID='172.31.252.12' PLUTO_MY_CLIENT='172.31.252.12/32' PLUTO_MY_CLIENT_NET='172.31.252.12' PLUTO_MY_CLIENT_MASK='255.255.255.255' PLUTO_MY_PORT='1701' PLUTO_MY_PROTOCOL='17' PLUTO_PEER='172.16.10.240' PLUTO_PEER_ID='192.168.1.10' PLUTO_PEER_CLIENT='192.168.1.10/32' PLUTO_PEER_CLIENT_NET='192.168.1.10' PLUTO_PEER_CLIENT_MASK='255.255.255.255' PLUTO_PEER_PORT='1701' PLUTO_PEER_PROTOCOL='17' PLUTO_PEER_CA='' PLUTO_STACK='netkey'   PLUTO_CONN_POLICY='PSK+ENCRYPT+DONTREKEY+IKEv2ALLOW+SAREFTRACK' PLUTO_CONN_ADDRFAMILY='ipv4'   PLUTO_IS_PEER_CISCO='0' PLUTO_CISCO_DNS_INFO='' PLUTO_CISCO_DOMAIN_INFO='' PLUTO_PEER_BANNER='' PLUTO_NM_CONFIGURED='0' ipsec _updown
Dec 18 10:38:07 ubuntu pluto[5476]: | popen(): cmd is 829 chars long
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd(   0):2>&1 PLUTO_VERB='unroute-host' PLUTO_VERSION='2.0' PLUTO_CONNECTION='L2TP-PSK-NA:
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd(  80):T' PLUTO_INTERFACE='eth0' PLUTO_NEXT_HOP='172.31.252.1' PLUTO_ME='172.31.252.12':
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd( 160): PLUTO_MY_ID='172.31.252.12' PLUTO_MY_CLIENT='172.31.252.12/32' PLUTO_MY_CLIENT_:
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd( 240):NET='172.31.252.12' PLUTO_MY_CLIENT_MASK='255.255.255.255' PLUTO_MY_PORT='1701' :
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd( 320):PLUTO_MY_PROTOCOL='17' PLUTO_PEER='172.16.10.240' PLUTO_PEER_ID='192.168.1.10' P:
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd( 400):LUTO_PEER_CLIENT='192.168.1.10/32' PLUTO_PEER_CLIENT_NET='192.168.1.10' PLUTO_PE:
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd( 480):ER_CLIENT_MASK='255.255.255.255' PLUTO_PEER_PORT='1701' PLUTO_PEER_PROTOCOL='17':
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd( 560): PLUTO_PEER_CA='' PLUTO_STACK='netkey'   PLUTO_CONN_POLICY='PSK+ENCRYPT+DONTREKE:
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd( 640):Y+IKEv2ALLOW+SAREFTRACK' PLUTO_CONN_ADDRFAMILY='ipv4'   PLUTO_IS_PEER_CISCO='0' :
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd( 720)PLUTO_CISCO_DNS_INFO='' PLUTO_CISCO_DOMAIN_INFO='' PLUTO_PEER_BANNER='' PLUTO_NM:
Dec 18 10:38:07 ubuntu pluto[5476]: | cmd( 800):_CONFIGURED='0' ipsec _updown:
Dec 18 10:38:07 ubuntu pluto[5476]: | delete inbound eroute 192.168.1.10/32:1701 --17-> 172.31.252.12/32:1701 => unk255.10000@172.31.252.12 (raw_eroute)
Dec 18 10:38:07 ubuntu pluto[5476]: | raw_eroute result=1 
Dec 18 10:38:07 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: received and ignored informational message
Dec 18 10:38:07 ubuntu pluto[5476]: | complete state transition with STF_IGNORE
Dec 18 10:38:07 ubuntu pluto[5476]: | * processed 0 messages from cryptographic helpers 
Dec 18 10:38:07 ubuntu pluto[5476]: | next event EVENT_NAT_T_KEEPALIVE in 5 seconds
Dec 18 10:38:07 ubuntu pluto[5476]: | next event EVENT_NAT_T_KEEPALIVE in 5 seconds
Dec 18 10:38:07 ubuntu pluto[5476]: |  
Dec 18 10:38:07 ubuntu pluto[5476]: | *received 92 bytes from 172.16.10.240:4500 on eth0 (port=4500)
Dec 18 10:38:07 ubuntu pluto[5476]: |  processing version=1.0 packet with exchange type=ISAKMP_XCHG_INFO (5)
Dec 18 10:38:07 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:38:07 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:38:07 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:38:07 ubuntu pluto[5476]: | peer and cookies match on #1, provided msgid 00000000 vs 00000000/00000000
Dec 18 10:38:07 ubuntu pluto[5476]: | p15 state object #1 found, in STATE_MAIN_R3
Dec 18 10:38:07 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:38:07 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:38:07 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:38:07 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:38:07 ubuntu pluto[5476]: | v1 peer and cookies match on #1, provided msgid 00000000 vs 00000000
Dec 18 10:38:07 ubuntu pluto[5476]: | v1 state object #1 found, in STATE_MAIN_R3
Dec 18 10:38:07 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:38:07 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240 #1: received Delete SA payload: deleting ISAKMP State #1
Dec 18 10:38:07 ubuntu pluto[5476]: | deleting state #1
Dec 18 10:38:07 ubuntu pluto[5476]: | sending 92 bytes for delete notify through eth0:4500 to 172.16.10.240:4500 (using #1)
Dec 18 10:38:07 ubuntu pluto[5476]: | ICOOKIE:  fd f4 24 68  b5 e7 88 48
Dec 18 10:38:07 ubuntu pluto[5476]: | RCOOKIE:  7f 35 7e 46  58 b6 2e e8
Dec 18 10:38:07 ubuntu pluto[5476]: | state hash entry 11
Dec 18 10:38:07 ubuntu pluto[5476]: | processing connection L2TP-PSK-NAT[2] 172.16.10.240
Dec 18 10:38:07 ubuntu pluto[5476]: "L2TP-PSK-NAT"[2] 172.16.10.240: deleting connection "L2TP-PSK-NAT" instance with peer 172.16.10.240 {isakmp=#0/ipsec=#0}
Dec 18 10:38:07 ubuntu pluto[5476]: packet from 172.16.10.240:4500: received and ignored informational message
Dec 18 10:38:07 ubuntu pluto[5476]: | complete state transition with STF_IGNORE
Dec 18 10:38:07 ubuntu pluto[5476]: | * processed 0 messages from cryptographic helpers 
Dec 18 10:38:07 ubuntu pluto[5476]: | next event EVENT_NAT_T_KEEPALIVE in 5 seconds

```


_**Openswan config is:**_

/etc/ipsec.conf

```

version 2.0


config setup
    dumpdir=/var/run/pluto/
    plutodebug=control
    nat_traversal=yes
    oe=off
    protostack=netkey
    nhelpers=0
  
conn L2TP-PSK-NAT
    rightsubnet=vhost:%priv
    also=L2TP-PSK-noNAT


conn L2TP-PSK-noNAT
    authby=secret
    pfs=no
    auto=add
    keyingtries=3
    rekey=no
    dpddelay=30
    dpdtimeout=120
    dpdaction=clear
    ikelifetime=8h
    keylife=1h
    type=transport
    left=%defaultroute
    leftnexthop=%defaultroute
    leftprotoport=17/1701
    right=%any
    rightprotoport=17/%any
    forceencaps=yes

```

/etc/ipsec.secrets

```
172.31.252.12        %any:         "password"

```


/etc/xl2tpd/xl2tpd.conf
```

[global]
 ipsec saref = no

[lns default]
ip range = 192.168.171.10-192.168.171.20
local ip = 192.168.171.1
refuse chap = yes
refuse pap = yes
require authentication = yes
ppp debug = yes
pppoptfile = /etc/ppp/options.l2tpd
length bit = yes

```

/etc/ppp/options.l2tpd
 ```
require-mschap-v2
refuse-mschap
ms-dns 172.31.0.100
ms-dns 172.31.4.100
asyncmap 0
auth
crtscts
lock
hide-password
modem
debug
name l2tpd
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
mtu 1380
mru 1380
plugin radius.so

```

/etc/radiusclient/radiusclient.conf
 ```
auth_order      radius,local
login_tries     4
login_timeout   60
nologin         /etc/nologin
issue           /etc/radiusclient/issue
authserver      172.31.252.100:1812
acctserver      172.31.252.100:1813
servers         /etc/radiusclient/servers
dictionary      /etc/radiusclient/dictionary
login_radius    /usr/sbin/login.radius
seqfile         /var/run/radius.seq
mapfile         /etc/radiusclient/port-id-map
default_realm
radius_timeout  10
radius_retries  3
login_local     /bin/login

```
/etc/radiusclient/servers
```

172.31.252.100            intralot2007

```

/etc/radiusclient/dictionary.microsoft
 ```
#
#       Microsoft's VSA's, from RFC 2548
#
#       $Id: dictionary.microsoft,v 1.1 2002/03/06 13:23:09 dfs Exp $
#
 
VENDOR          Microsoft       311     Microsoft
 
ATTRIBUTE       MS-CHAP-Response        1       string  Microsoft
ATTRIBUTE       MS-CHAP-Error           2       string  Microsoft
ATTRIBUTE       MS-CHAP-CPW-1           3       string  Microsoft
ATTRIBUTE       MS-CHAP-CPW-2           4       string  Microsoft
ATTRIBUTE       MS-CHAP-LM-Enc-PW       5       string  Microsoft
ATTRIBUTE       MS-CHAP-NT-Enc-PW       6       string  Microsoft
ATTRIBUTE       MS-MPPE-Encryption-Policy 7     string  Microsoft
# This is referred to as both singular and plural in the RFC.
# Plural seems to make more sense.
ATTRIBUTE       MS-MPPE-Encryption-Type 8       string  Microsoft
ATTRIBUTE       MS-MPPE-Encryption-Types  8     string  Microsoft
ATTRIBUTE       MS-RAS-Vendor           9       integer Microsoft
ATTRIBUTE       MS-CHAP-Domain          10      string  Microsoft
ATTRIBUTE       MS-CHAP-Challenge       11      string  Microsoft
ATTRIBUTE       MS-CHAP-MPPE-Keys       12      string  Microsoft
ATTRIBUTE       MS-BAP-Usage            13      integer Microsoft
ATTRIBUTE       MS-Link-Utilization-Threshold 14 integer        Microsoft
ATTRIBUTE       MS-Link-Drop-Time-Limit 15      integer Microsoft
ATTRIBUTE       MS-MPPE-Send-Key        16      string  Microsoft
ATTRIBUTE       MS-MPPE-Recv-Key        17      string  Microsoft
ATTRIBUTE       MS-RAS-Version          18      string  Microsoft
ATTRIBUTE       MS-Old-ARAP-Password    19      string  Microsoft
ATTRIBUTE       MS-New-ARAP-Password    20      string  Microsoft
ATTRIBUTE       MS-ARAP-PW-Change-Reason 21     integer Microsoft
 
ATTRIBUTE       MS-Filter               22      string  Microsoft
ATTRIBUTE       MS-Acct-Auth-Type       23      integer Microsoft
ATTRIBUTE       MS-Acct-EAP-Type        24      integer Microsoft
 
ATTRIBUTE       MS-CHAP2-Response       25      string  Microsoft
ATTRIBUTE       MS-CHAP2-Success        26      string  Microsoft
ATTRIBUTE       MS-CHAP2-CPW            27      string  Microsoft
 
ATTRIBUTE       MS-Primary-DNS-Server   28      ipaddr  Microsoft
ATTRIBUTE       MS-Secondary-DNS-Server 29      ipaddr  Microsoft
ATTRIBUTE       MS-Primary-NBNS-Server  30      ipaddr  Microsoft
ATTRIBUTE       MS-Secondary-NBNS-Server 31     ipaddr  Microsoft
 
ATTRIBUTE      MS-ARAP-Challenge       33      string  Microsoft
 
#
#       Integer Translations
#
 
#       MS-BAP-Usage Values
 
VALUE           MS-BAP-Usage            Not-Allowed     0
VALUE           MS-BAP-Usage            Allowed         1
VALUE           MS-BAP-Usage            Required        2
 
#       MS-ARAP-Password-Change-Reason Values
 
VALUE   MS-ARAP-PW-Change-Reason        Just-Change-Password            1
VALUE   MS-ARAP-PW-Change-Reason        Expired-Password                2
VALUE   MS-ARAP-PW-Change-Reason        Admin-Requires-Password-Change  3
VALUE   MS-ARAP-PW-Change-Reason        Password-Too-Short              4
 
#       MS-Acct-Auth-Type Values
 
VALUE           MS-Acct-Auth-Type       PAP             1
VALUE           MS-Acct-Auth-Type       CHAP            2
VALUE           MS-Acct-Auth-Type       MS-CHAP-1       3
VALUE           MS-Acct-Auth-Type       MS-CHAP-2       4
VALUE           MS-Acct-Auth-Type       EAP             5
 
#       MS-Acct-EAP-Type Values
 
VALUE           MS-Acct-EAP-Type        MD5             4
VALUE           MS-Acct-EAP-Type        OTP             5
VALUE           MS-Acct-EAP-Type        Generic-Token-Card      6
VALUE           MS-Acct-EAP-Type        TLS             13

```


_**Any idea for this?**_

---

### Post by philinux on 2013-12-18
Please use code tags. Thats the # icon in the post editor.

---

