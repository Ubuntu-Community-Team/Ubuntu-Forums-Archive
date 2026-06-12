---
title: "site 2 site tunnel with IPsec, racoon and NAT"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by D43m0n on 2007-08-06
Hi everyone,

I'm struggling for a while now and can't seem to find any answer. I hope someone has a (few?) suggestion(s).

Here's the situation:

I've got a server running feisty with racoon and ipsec-tools. The server is behind a Alcatel/Speedtouch ADSL modem. I've setup portforwarding from the ADSL modem to my server. I've also added ports 4500 and the ESP protocol in the modem. The server has one NIC installed BTW.

The company site has a full public B address. There is not NAT used at all. I'm using a pre-shared-key to authenticate.

phase I doesn't even succeed with racoon.

Here are my config files:
psk file:
```
ip.of.vpn.gateway ihfmxefhe
```

racoon conf:
```
path pre_shared_key "/etc/racoon/psk.txt";

log notify;
padding
{
        maximum_length 20;      # maximum padding length.
        randomize off;          # enable randomize length.
        strict_check off;       # enable strict check.
        exclusive_tail off;     # extract last one octet.
}

timer
{
        # These value can be changed per remote node.
        counter 5;              # maximum trying count to send.
        interval 20 sec;        # maximum interval to resend.
        persend 1;              # the number of packets per a send.
        natt_keepalive 10 sec;

        # timer for waiting to complete each phase.
        phase1 30 sec;
        phase2 15 sec;
}
remote ip.of.vpn.gateway
{
        exchange_mode main,aggressive,base;

        nat_traversal on;
        lifetime time 28800 sec;
        initial_contact on;
        proposal_check obey;
        proposal {
                encryption_algorithm 3des;
                hash_algorithm sha1;
                authentication_method pre_shared_key;
                dh_group 2;
        }
}

sainfo address 192.168.1.0/24 any address company.network.address/16 any
{
        pfs_group 2;
        lifetime time 28800 sec;
        encryption_algorithm 3des;
        authentication_algorithm hmac_sha1;
        compression_algorithm deflate;
}
```

and finally, setkey configuration:
```
flush;
spdflush;
spdadd company.network.address/16 192.168.1.0/24 any -P in ipsec 
esp/tunnel/ip.of.vpn.gateway-192.168.1.60/require;
spdadd 192.168.1.0/24 company.network.address/16 any -P out ipsec 
esp/tunnel/192.168.1.60-ip.of.vpn.gateway/require;
```

my side uses NAT, the company's side uses no NAT. Is that possible? I'm starting to think that if you're using NAT, you need to use it on both ends.
I haven't added any (static) ip routes for traffic that goes through the tunnel. From what I've understood, that shouldn't be necessary since the kernel uses the SPD's to decide what needs to be protected.

Am I missing out on something in my configuration? The fact that NAT is involved on my side makes it a bit confusing...

Thanks in advance!

---

### Post by mips on 2007-08-06
> **D43m0n said:**
> I'm starting to think that if you're using NAT, you need to use it on both ends.



Definately not the case.

What does the racoon log files say ?

[http://www.howtoforge.com/racoon_roadwarrior_vpn](http://www.howtoforge.com/racoon_roadwarrior_vpn)
[http://www.ipsec-howto.org/x304.html](http://www.ipsec-howto.org/x304.html)   See NAT-Traversal

PS. I think you might need static routes

---

### Post by D43m0n on 2007-08-06
this is racoon output at starting up:

```
 racoon -F -d -f racoon.conf
Foreground mode.
2007-08-06 23:59:23: INFO: @(#)ipsec-tools 0.6.6 (http://ipsec-tools.sourceforge.net)
2007-08-06 23:59:23: INFO: @(#)This product linked OpenSSL 0.9.8c 05 Sep 2006 (http://www.openssl.org/)
2007-08-06 23:59:23: DEBUG: call pfkey_send_register for AH
2007-08-06 23:59:23: DEBUG: call pfkey_send_register for ESP
2007-08-06 23:59:24: DEBUG: call pfkey_send_register for IPCOMP
2007-08-06 23:59:24: DEBUG: reading config file racoon.conf
2007-08-06 23:59:24: DEBUG: hmac(modp1024)
2007-08-06 23:59:24: DEBUG: compression algorithm can not be checked because sadb message doesn't support it.
2007-08-06 23:59:24: DEBUG: open /var/run/racoon/racoon.sock as racoon management.
2007-08-06 23:59:24: DEBUG: my interface: fe80::20a:5eff:fe3f:d723%eth0 (eth0)
2007-08-06 23:59:24: DEBUG: my interface: ::1 (lo)
2007-08-06 23:59:24: DEBUG: my interface: 192.168.1.60 (eth0)
2007-08-06 23:59:24: DEBUG: my interface: 127.0.0.1 (lo)
2007-08-06 23:59:24: DEBUG: configuring default isakmp port.
2007-08-06 23:59:24: NOTIFY: NAT-T is enabled, autoconfiguring ports
2007-08-06 23:59:24: DEBUG: 8 addrs are configured successfully
2007-08-06 23:59:24: INFO: 127.0.0.1[500] used as isakmp port (fd=6)
2007-08-06 23:59:24: INFO: 127.0.0.1[500] used for NAT-T
2007-08-06 23:59:24: INFO: 127.0.0.1[4500] used as isakmp port (fd=7)
2007-08-06 23:59:24: INFO: 127.0.0.1[4500] used for NAT-T
2007-08-06 23:59:24: INFO: 192.168.1.60[500] used as isakmp port (fd=8)
2007-08-06 23:59:24: INFO: 192.168.1.60[500] used for NAT-T
2007-08-06 23:59:24: INFO: 192.168.1.60[4500] used as isakmp port (fd=9)
2007-08-06 23:59:24: INFO: 192.168.1.60[4500] used for NAT-T
2007-08-06 23:59:24: INFO: ::1[500] used as isakmp port (fd=10)
2007-08-06 23:59:24: INFO: ::1[4500] used as isakmp port (fd=11)
2007-08-06 23:59:24: INFO: fe80::20a:5eff:fe3f:d723%eth0[500] used as isakmp port (fd=12)
2007-08-06 23:59:24: INFO: fe80::20a:5eff:fe3f:d723%eth0[4500] used as isakmp port (fd=13)
2007-08-06 23:59:24: DEBUG: get pfkey X_SPDDUMP message
2007-08-06 23:59:24: DEBUG: get pfkey X_SPDDUMP message
2007-08-06 23:59:24: DEBUG: sub:0xbf849d4c: 192.168.1.0/24[0] company.network.address/16[0] proto=any dir=out
2007-08-06 23:59:24: DEBUG: db :0x80bea58: company.network.address/16[0] 192.168.1.0/24[0] proto=any dir=in
2007-08-06 23:59:24: DEBUG: get pfkey X_SPDDUMP message
2007-08-06 23:59:24: DEBUG: sub:0xbf849d4c: company.network.address/16[0] 192.168.1.0/24[0] proto=any dir=fwd
2007-08-06 23:59:24: DEBUG: db :0x80bea58: company.network.address/16[0] 192.168.1.0/24[0] proto=any dir=in
2007-08-06 23:59:24: DEBUG: sub:0xbf849d4c: company.network.address/16[0] 192.168.1.0/24[0] proto=any dir=fwd
2007-08-06 23:59:24: DEBUG: db :0x80bf4e0: 192.168.1.0/24[0] company.network.address/16[0] proto=any dir=out
```

this is what racoon says when I try to ping any host on the company network (I'm pinging from the server itself, no special routes or extra aliased addresses setup):

```
2007-08-07 00:03:58: DEBUG: get pfkey ACQUIRE message
2007-08-07 00:03:58: DEBUG: suitable outbound SP found: 192.168.1.0/24[0] company.network.address/16[0] proto=any dir=out.
2007-08-07 00:03:58: DEBUG: sub:0xbf849d4c: company.network.address/16[0] 192.168.1.0/24[0] proto=any dir=in
2007-08-07 00:03:58: DEBUG: db :0x80bea58: company.network.address/16[0] 192.168.1.0/24[0] proto=any dir=in
2007-08-07 00:03:58: DEBUG: suitable inbound SP found: company.network.address/16[0] 192.168.1.0/24[0] proto=any dir=in.
2007-08-07 00:03:58: DEBUG: new acquire 192.168.1.0/24[0] company.network.address/16[0] proto=any dir=out
2007-08-07 00:03:58: DEBUG:  (proto_id=ESP spisize=4 spi=00000000 spi_p=00000000 encmode=Tunnel reqid=0:0)
2007-08-07 00:03:58: DEBUG:   (trns_id=3DES encklen=0 authtype=hmac-sha)
2007-08-07 00:03:58: DEBUG: configuration found for ip.of.vpn.gateway.
2007-08-07 00:03:58: INFO: IPsec-SA request for ip.of.vpn.gateway queued due to no phase1 found.
2007-08-07 00:03:58: DEBUG: ===
2007-08-07 00:03:58: INFO: initiate new phase 1 negotiation: 192.168.1.60[500]<=>ip.of.vpn.gateway[500]
2007-08-07 00:03:58: INFO: begin Identity Protection mode.
2007-08-07 00:03:58: DEBUG: new cookie:
800d8ae83243773b
2007-08-07 00:03:58: DEBUG: add payload of len 48, next type 13
2007-08-07 00:03:58: DEBUG: add payload of len 16, next type 13
2007-08-07 00:03:58: DEBUG: add payload of len 16, next type 13
2007-08-07 00:03:58: DEBUG: add payload of len 16, next type 13
2007-08-07 00:03:58: DEBUG: add payload of len 16, next type 13
2007-08-07 00:03:58: DEBUG: add payload of len 16, next type 0
2007-08-07 00:03:58: DEBUG: 180 bytes from 192.168.1.60[500] to ip.of.vpn.gateway[500]
2007-08-07 00:03:58: DEBUG: sockname 192.168.1.60[500]
2007-08-07 00:03:58: DEBUG: send packet from 192.168.1.60[500]
2007-08-07 00:03:58: DEBUG: send packet to ip.of.vpn.gateway[500]
2007-08-07 00:03:58: DEBUG: src4 192.168.1.60[500]
2007-08-07 00:03:58: DEBUG: dst4 ip.of.vpn.gateway[500]
2007-08-07 00:03:58: DEBUG: 1 times of 180 bytes message will be sent to ip.of.vpn.gateway[500]
2007-08-07 00:03:58: DEBUG:
800d8ae8 3243773b 00000000 00000000 01100200 00000000 000000b4 0d000034
00000001 00000001 00000028 01010001 00000020 01010000 800b0001 800c7080
80010005 80030001 80020002 80040002 0d000014 4a131c81 07035845 5c5728f2
0e95452f 0d000014 cd604643 35df21f8 7cfdb2fc 68b6a448 0d000014 90cb8091
3ebb696e 086381b5 ec427b1f 0d000014 4485152d 18b6bbcd 0be8a846 9579ddcc
00000014 afcad713 68a1f1c9 6b8696fc 77570100
2007-08-07 00:03:58: DEBUG: resend phase1 packet 800d8ae83243773b:0000000000000000
2007-08-07 00:04:18: DEBUG: 180 bytes from 192.168.1.60[500] to ip.of.vpn.gateway[500]
2007-08-07 00:04:18: DEBUG: sockname 192.168.1.60[500]
2007-08-07 00:04:18: DEBUG: send packet from 192.168.1.60[500]
2007-08-07 00:04:18: DEBUG: send packet to ip.of.vpn.gateway[500]
2007-08-07 00:04:18: DEBUG: src4 192.168.1.60[500]
2007-08-07 00:04:18: DEBUG: dst4 ip.of.vpn.gateway[500]
2007-08-07 00:04:18: DEBUG: 1 times of 180 bytes message will be sent to ip.of.vpn.gateway[500]
2007-08-07 00:04:18: DEBUG:
800d8ae8 3243773b 00000000 00000000 01100200 00000000 000000b4 0d000034
00000001 00000001 00000028 01010001 00000020 01010000 800b0001 800c7080
80010005 80030001 80020002 80040002 0d000014 4a131c81 07035845 5c5728f2
0e95452f 0d000014 cd604643 35df21f8 7cfdb2fc 68b6a448 0d000014 90cb8091
3ebb696e 086381b5 ec427b1f 0d000014 4485152d 18b6bbcd 0be8a846 9579ddcc
00000014 afcad713 68a1f1c9 6b8696fc 77570100
2007-08-07 00:04:18: DEBUG: resend phase1 packet 800d8ae83243773b:0000000000000000
2007-08-07 00:04:29: ERROR: phase2 negotiation failed due to time up waiting for phase1. ESP ip.of.vpn.gateway[500]->192.168.1.60[500]
2007-08-07 00:04:29: INFO: delete phase 2 handler.
2007-08-07 00:04:38: DEBUG: 180 bytes from 192.168.1.60[500] to ip.of.vpn.gateway[500]
2007-08-07 00:04:38: DEBUG: sockname 192.168.1.60[500]
2007-08-07 00:04:38: DEBUG: send packet from 192.168.1.60[500]
2007-08-07 00:04:38: DEBUG: send packet to ip.of.vpn.gateway[500]
2007-08-07 00:04:38: DEBUG: src4 192.168.1.60[500]
2007-08-07 00:04:38: DEBUG: dst4 ip.of.vpn.gateway[500]
2007-08-07 00:04:38: DEBUG: 1 times of 180 bytes message will be sent to ip.of.vpn.gateway[500]
2007-08-07 00:04:38: DEBUG:
800d8ae8 3243773b 00000000 00000000 01100200 00000000 000000b4 0d000034
00000001 00000001 00000028 01010001 00000020 01010000 800b0001 800c7080
80010005 80030001 80020002 80040002 0d000014 4a131c81 07035845 5c5728f2
0e95452f 0d000014 cd604643 35df21f8 7cfdb2fc 68b6a448 0d000014 90cb8091
3ebb696e 086381b5 ec427b1f 0d000014 4485152d 18b6bbcd 0be8a846 9579ddcc
00000014 afcad713 68a1f1c9 6b8696fc 77570100
2007-08-07 00:04:38: DEBUG: resend phase1 packet 800d8ae83243773b:0000000000000000
2007-08-07 00:04:58: DEBUG: 180 bytes from 192.168.1.60[500] to ip.of.vpn.gateway[500]
2007-08-07 00:04:58: DEBUG: sockname 192.168.1.60[500]
2007-08-07 00:04:58: DEBUG: send packet from 192.168.1.60[500]
2007-08-07 00:04:58: DEBUG: send packet to ip.of.vpn.gateway[500]
2007-08-07 00:04:58: DEBUG: src4 192.168.1.60[500]
2007-08-07 00:04:58: DEBUG: dst4 ip.of.vpn.gateway[500]
2007-08-07 00:04:58: DEBUG: 1 times of 180 bytes message will be sent to ip.of.vpn.gateway[500]
2007-08-07 00:04:58: DEBUG:
800d8ae8 3243773b 00000000 00000000 01100200 00000000 000000b4 0d000034
00000001 00000001 00000028 01010001 00000020 01010000 800b0001 800c7080
80010005 80030001 80020002 80040002 0d000014 4a131c81 07035845 5c5728f2
0e95452f 0d000014 cd604643 35df21f8 7cfdb2fc 68b6a448 0d000014 90cb8091
3ebb696e 086381b5 ec427b1f 0d000014 4485152d 18b6bbcd 0be8a846 9579ddcc
00000014 afcad713 68a1f1c9 6b8696fc 77570100
2007-08-07 00:04:58: DEBUG: resend phase1 packet 800d8ae83243773b:0000000000000000
2007-08-07 00:05:18: DEBUG: 180 bytes from 192.168.1.60[500] to ip.of.vpn.gateway[500]
2007-08-07 00:05:18: DEBUG: sockname 192.168.1.60[500]
2007-08-07 00:05:18: DEBUG: send packet from 192.168.1.60[500]
2007-08-07 00:05:18: DEBUG: send packet to ip.of.vpn.gateway[500]
2007-08-07 00:05:18: DEBUG: src4 192.168.1.60[500]
2007-08-07 00:05:18: DEBUG: dst4 ip.of.vpn.gateway[500]
2007-08-07 00:05:18: DEBUG: 1 times of 180 bytes message will be sent to ip.of.vpn.gateway[500]
2007-08-07 00:05:18: DEBUG:
800d8ae8 3243773b 00000000 00000000 01100200 00000000 000000b4 0d000034
00000001 00000001 00000028 01010001 00000020 01010000 800b0001 800c7080
80010005 80030001 80020002 80040002 0d000014 4a131c81 07035845 5c5728f2
0e95452f 0d000014 cd604643 35df21f8 7cfdb2fc 68b6a448 0d000014 90cb8091
3ebb696e 086381b5 ec427b1f 0d000014 4485152d 18b6bbcd 0be8a846 9579ddcc
00000014 afcad713 68a1f1c9 6b8696fc 77570100
2007-08-07 00:05:18: DEBUG: resend phase1 packet 800d8ae83243773b:0000000000000000
2007-08-07 00:05:38: DEBUG: 180 bytes from 192.168.1.60[500] to ip.of.vpn.gateway[500]
2007-08-07 00:05:38: DEBUG: sockname 192.168.1.60[500]
2007-08-07 00:05:38: DEBUG: send packet from 192.168.1.60[500]
2007-08-07 00:05:38: DEBUG: send packet to ip.of.vpn.gateway[500]
2007-08-07 00:05:38: DEBUG: src4 192.168.1.60[500]
2007-08-07 00:05:38: DEBUG: dst4 ip.of.vpn.gateway[500]
2007-08-07 00:05:38: DEBUG: 1 times of 180 bytes message will be sent to ip.of.vpn.gateway[500]
2007-08-07 00:05:38: DEBUG:
800d8ae8 3243773b 00000000 00000000 01100200 00000000 000000b4 0d000034
00000001 00000001 00000028 01010001 00000020 01010000 800b0001 800c7080
80010005 80030001 80020002 80040002 0d000014 4a131c81 07035845 5c5728f2
0e95452f 0d000014 cd604643 35df21f8 7cfdb2fc 68b6a448 0d000014 90cb8091
3ebb696e 086381b5 ec427b1f 0d000014 4485152d 18b6bbcd 0be8a846 9579ddcc
00000014 afcad713 68a1f1c9 6b8696fc 77570100
2007-08-07 00:05:38: DEBUG: resend phase1 packet 800d8ae83243773b:0000000000000000
```

I don't see any real errors, but then again, I haven't seen racoon output on a regular basis (yet).

Thanks

---

### Post by mips on 2007-08-06
[QUOTE=D43m0n;3144567]
I don't see any real errors, but then again, I haven't seen racoon output on a regular basis (yet).
/QUOTE]

This is the first time in my life I looked at racoon logs. I see no blatant errors but then again this is all new to me.


Do you know of any public VPN one can connect to to test racoon/ipsec/nat-t with. If there is one I would be willing to install it on my box to test as I'm also behind a nat router.

---

### Post by D43m0n on 2007-08-07
> **mips said:**
> 
Do you know of any public VPN one can connect to to test racoon/ipsec/nat-t with.


I don't know about any "public VPN". I can't imagine that anyone would run a public VPN site.

---

### Post by mips on 2007-08-07
> **D43m0n said:**
> I don't know about any "public VPN". I can't imagine that anyone would run a public VPN site.

I'm talking about a testbed environment.

---

