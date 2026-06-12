---
title: "Site to Site Ipsec Openswan and Azure disconnecting every hour"
date: 2014-05-13
forum: Networking &amp; Wireless
---

### Post by Zenwo on 2014-05-13
Hi there !


I have some issue with my Openswan.


I'm using an openswan (ubuntu) on aws as hub vpn to connect my offices to azure.


Connections with offices works without issues.


Connection with Azure works but disconnect every hour, i have to restart ipsec service to make it up again.


My ipsec.conf :


    ```
config setup
      protostack=netkey
      nat_traversal=yes
      virtual_private=%v4:172.16.0.0/24
      oe=off
 
      include /etc/ipsec.d/*.conf

```

My openswan to azure conf :


    ```
conn amznazure
        authby=secret
        auto=start
        type=tunnel
        left=%defaultroute 
        leftsubnets=172.16.0.0/24,192.168.16.0/24,192.168.31.0/24,192.168.29.0/24,192.168.13.0/24,192.168.30.0/24,192.168.11.0/24,192.168.33.0/24
        leftnexthop=%defaultroute
        right="myazuregatewayhere"
        rightsubnet=10.1.254.0/24
        ike=aes128-sha1-modp1024
        esp=aes128-sha1
        pfs=n
```o


My auth.log at disconnecting point :


    ```
May 13 15:06:46 ip-172-16-0-215 pluto[26141]: "amznazure/8x0" #172: received Delete SA payload: replace IPSEC State #181 in 10 seconds
    May 13 15:06:46 ip-172-16-0-215 pluto[26141]: "amznazure/8x0" #172: received and ignored informational message
    May 13 15:06:54 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #68: the peer proposed: 192.168.16.0/24:0/0 -> 10.1.0.0/16:0/0
    May 13 15:06:54 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #194: responding to Quick Mode proposal {msgid:05000000}
    May 13 15:06:54 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #194:     us: 172.16.0.0/24===172.16.0.215---172.16.0.1
    May 13 15:06:54 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #194:   them: 137.117.216.139<137.117.216.139>===10.1.254.0/24
    May 13 15:06:54 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #194: keeping refhim=4294901761 during rekey
    May 13 15:06:54 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #194: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
    May 13 15:06:54 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #194: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
    May 13 15:06:54 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #194: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
    May 13 15:06:54 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #194: STATE_QUICK_R2: IPsec SA established tunnel mode {ESP=>0x6c02e964 <0xd39ebc95 xfrm=AES_256-HMAC_SHA2_256 NATOA=none NATD=137.117.216.139:4500 DPD=none}
    May 13 15:06:56 ip-172-16-0-215 pluto[26141]: "amznazure/2x0" #195: initiating Quick Mode PSK+ENCRYPT+TUNNEL+UP+IKEv2ALLOW+SAREFTRACK to replace #181 {using isakmp#172 msgid:fd85910c proposal=AES(12)_128-SHA1(2)_160 pfsgroup=no-pfs}
    May 13 15:06:56 ip-172-16-0-215 pluto[26141]: "amznazure/2x0" #195: IKE message has the Commit Flag set but Pluto doesn't implement this feature; ignoring flag
    May 13 15:06:56 ip-172-16-0-215 pluto[26141]: "amznazure/2x0" #195: ignoring informational payload, type IPSEC_RESPONDER_LIFETIME msgid=fd85910c
    May 13 15:06:56 ip-172-16-0-215 pluto[26141]: "amznazure/2x0" #195: transition from state STATE_QUICK_I1 to state STATE_QUICK_I2
    May 13 15:06:56 ip-172-16-0-215 pluto[26141]: "amznazure/2x0" #195: STATE_QUICK_I2: sent QI2, IPsec SA established tunnel mode {ESP=>0x8e84d9d4 <0x36a23a30 xfrm=AES_128-HMAC_SHA1 NATOA=none NATD=none DPD=none}
    May 13 15:06:56 ip-172-16-0-215 pluto[26141]: "amznazure/2x0" #195: IKE message has the Commit Flag set but Pluto doesn't implement this feature; ignoring flag
    May 13 15:06:56 ip-172-16-0-215 pluto[26141]: "amznazure/2x0" #195: message ignored because it contains an unexpected payload type (ISAKMP_NEXT_HASH)
    May 13 15:06:56 ip-172-16-0-215 pluto[26141]: "amznazure/2x0" #195: sending encrypted notification INVALID_PAYLOAD_TYPE to 137.117.216.139:4500
    May 13 15:06:56 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #68: received Delete SA payload: replace IPSEC State #194 in 10 seconds
    May 13 15:06:56 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #68: received and ignored informational message
    May 13 15:07:06 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #196: initiating Quick Mode PSK+ENCRYPT+TUNNEL+UP+IKEv2ALLOW+SAREFTRACK to replace #194 {using isakmp#172 msgid:b9cad2db proposal=AES(12)_128-SHA1(2)_160 pfsgroup=no-pfs}
    May 13 15:07:06 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #196: IKE message has the Commit Flag set but Pluto doesn't implement this feature; ignoring flag
    May 13 15:07:06 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #196: ignoring informational payload, type IPSEC_RESPONDER_LIFETIME msgid=b9cad2db
    May 13 15:07:06 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #196: transition from state STATE_QUICK_I1 to state STATE_QUICK_I2
    May 13 15:07:06 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #196: STATE_QUICK_I2: sent QI2, IPsec SA established tunnel mode {ESP=>0xa08a87f8 <0x28981ffa xfrm=AES_128-HMAC_SHA1 NATOA=none NATD=none DPD=none}
    May 13 15:07:06 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #196: IKE message has the Commit Flag set but Pluto doesn't implement this feature; ignoring flag
    May 13 15:07:06 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #196: message ignored because it contains an unexpected payload type (ISAKMP_NEXT_HASH)
    May 13 15:07:06 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #196: sending encrypted notification INVALID_PAYLOAD_TYPE to 137.117.216.139:4500
    May 13 15:07:06 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #68: received Delete SA(0xd5a38e96) payload: deleting IPSEC State #158
    May 13 15:07:06 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #68: received and ignored informational message
    May 13 15:07:19 ip-172-16-0-215 pluto[26141]: "amzncapbreton/8x0" #193: max number of retransmissions (2) reached STATE_QUICK_I1.  No acceptable response to our first Quick Mode message: perhaps peer likes no proposal
    May 13 15:07:19 ip-172-16-0-215 pluto[26141]: "amzncapbreton/8x0" #193: starting keying attempt 48 of an unlimited number
    May 13 15:07:19 ip-172-16-0-215 pluto[26141]: "amzncapbreton/8x0" #197: initiating Quick Mode PSK+ENCRYPT+TUNNEL+PFS+UP+IKEv2ALLOW+SAREFTRACK to replace #193 {using isakmp#3 msgid:f20fa04b proposal=AES(12)_128-SHA1(2)_160 pfsgroup=OAKLEY_GROUP_MODP1024}
    May 13 15:08:01 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #198: initiating Main Mode to replace #68
    May 13 15:08:01 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #198: ignoring Vendor ID payload [MS NT5 ISAKMPOAKLEY 00000009]
    May 13 15:08:01 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #198: received Vendor ID payload [RFC 3947] method set to=115
    May 13 15:08:01 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #198: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 115
    May 13 15:08:01 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #198: ignoring Vendor ID payload [FRAGMENTATION]
    May 13 15:08:01 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #198: ignoring Vendor ID payload [MS-Negotiation Discovery Capable]
    May 13 15:08:01 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #198: ignoring Vendor ID payload [IKE CGA version 1]
    May 13 15:08:01 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #198: enabling possible NAT-traversal with method RFC 3947 (NAT-Traversal)
    May 13 15:08:01 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #198: transition from state STATE_MAIN_I1 to state STATE_MAIN_I2
    May 13 15:08:01 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #198: STATE_MAIN_I2: sent MI2, expecting MR2
    May 13 15:08:01 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #198: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike (MacOS X): i am NATed
    May 13 15:08:01 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #198: transition from state STATE_MAIN_I2 to state STATE_MAIN_I3
    May 13 15:08:01 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #198: STATE_MAIN_I3: sent MI3, expecting MR3
    May 13 15:08:01 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #198: Main mode peer ID is ID_IPV4_ADDR: '137.117.216.139'
    May 13 15:08:01 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #198: transition from state STATE_MAIN_I3 to state STATE_MAIN_I4
    May 13 15:08:01 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #198: STATE_MAIN_I4: ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_128 prf=oakley_sha group=modp1024}
    May 13 15:08:29 ip-172-16-0-215 pluto[26141]: "amzncapbreton/8x0" #197: max number of retransmissions (2) reached STATE_QUICK_I1.  No acceptable response to our first Quick Mode message: perhaps peer likes no proposal
    May 13 15:08:29 ip-172-16-0-215 pluto[26141]: "amzncapbreton/8x0" #197: starting keying attempt 49 of an unlimited number
    May 13 15:08:29 ip-172-16-0-215 pluto[26141]: "amzncapbreton/8x0" #199: initiating Quick Mode PSK+ENCRYPT+TUNNEL+PFS+UP+IKEv2ALLOW+SAREFTRACK to replace #197 {using isakmp#3 msgid:23e51653 proposal=AES(12)_128-SHA1(2)_160 pfsgroup=OAKLEY_GROUP_MODP1024}
    May 13 15:09:11 ip-172-16-0-215 pluto[26141]: "amznazure/8x0" #172: received Delete SA payload: replace IPSEC State #190 in 10 seconds
    May 13 15:09:11 ip-172-16-0-215 pluto[26141]: "amznazure/8x0" #172: received and ignored informational message
    May 13 15:09:21 ip-172-16-0-215 pluto[26141]: "amznazure/8x0" #200: initiating Quick Mode PSK+ENCRYPT+TUNNEL+UP+IKEv2ALLOW+SAREFTRACK to replace #190 {using isakmp#198 msgid:7b466d27 proposal=AES(12)_128-SHA1(2)_160 pfsgroup=no-pfs}
    May 13 15:09:21 ip-172-16-0-215 pluto[26141]: "amznazure/8x0" #200: IKE message has the Commit Flag set but Pluto doesn't implement this feature; ignoring flag
    May 13 15:09:21 ip-172-16-0-215 pluto[26141]: "amznazure/8x0" #200: ignoring informational payload, type IPSEC_RESPONDER_LIFETIME msgid=7b466d27
    May 13 15:09:21 ip-172-16-0-215 pluto[26141]: "amznazure/8x0" #200: transition from state STATE_QUICK_I1 to state STATE_QUICK_I2
    May 13 15:09:21 ip-172-16-0-215 pluto[26141]: "amznazure/8x0" #200: STATE_QUICK_I2: sent QI2, IPsec SA established tunnel mode {ESP=>0x05dc9dc4 <0x89727ec1 xfrm=AES_128-HMAC_SHA1 NATOA=none NATD=none DPD=none}
    May 13 15:09:21 ip-172-16-0-215 pluto[26141]: "amznazure/8x0" #200: IKE message has the Commit Flag set but Pluto doesn't implement this feature; ignoring flag
    May 13 15:09:21 ip-172-16-0-215 pluto[26141]: "amznazure/8x0" #200: message ignored because it contains an unexpected payload type (ISAKMP_NEXT_HASH)
    May 13 15:09:21 ip-172-16-0-215 pluto[26141]: "amznazure/8x0" #200: sending encrypted notification INVALID_PAYLOAD_TYPE to 137.117.216.139:4500
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/8x0" #1: received Delete SA payload: deleting ISAKMP State #1
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: packet from 137.117.216.139:4500: received and ignored informational message
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: packet from 137.117.216.139:4500: Informational Exchange is for an unknown (expired?) SA with MSGID:0xd38577ee
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: packet from 137.117.216.139:4500: Informational Exchange is for an unknown (expired?) SA with MSGID:0x1f7abcd4
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: packet from 137.117.216.139:4500: Informational Exchange is for an unknown (expired?) SA with MSGID:0x57162433
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: packet from 137.117.216.139:4500: Informational Exchange is for an unknown (expired?) SA with MSGID:0x824edc0a
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #68: the peer proposed: 192.168.13.0/24:0/0 -> 10.1.0.0/16:0/0
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #201: responding to Quick Mode proposal {msgid:06000000}
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #201:     us: 172.16.0.0/24===172.16.0.215---172.16.0.1
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #201:   them: 137.117.216.139<137.117.216.139>===10.1.254.0/24
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #201: keeping refhim=4294901761 during rekey
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #201: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #201: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #201: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #201: STATE_QUICK_R2: IPsec SA established tunnel mode {ESP=>0xc5cec1ca <0x2f21f49f xfrm=AES_256-HMAC_SHA2_256 NATOA=none NATD=137.117.216.139:4500 DPD=none}
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #68: the peer proposed: 192.168.11.0/24:0/0 -> 10.1.0.0/16:0/0
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #202: responding to Quick Mode proposal {msgid:07000000}
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #202:     us: 172.16.0.0/24===172.16.0.215---172.16.0.1
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #202:   them: 137.117.216.139<137.117.216.139>===10.1.254.0/24
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #202: keeping refhim=4294901761 during rekey
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #202: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #202: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #202: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #202: STATE_QUICK_R2: IPsec SA established tunnel mode {ESP=>0x56435fe4 <0x45266448 xfrm=AES_256-HMAC_SHA2_256 NATOA=none NATD=137.117.216.139:4500 DPD=none}
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #68: the peer proposed: 192.168.30.0/24:0/0 -> 10.1.0.0/16:0/0
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #203: responding to Quick Mode proposal {msgid:08000000}
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #203:     us: 172.16.0.0/24===172.16.0.215---172.16.0.1
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #203:   them: 137.117.216.139<137.117.216.139>===10.1.254.0/24
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #203: keeping refhim=4294901761 during rekey
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #203: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #203: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #203: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
    May 13 15:09:29 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #203: STATE_QUICK_R2: IPsec SA established tunnel mode {ESP=>0x3759acf8 <0xb80d6efa xfrm=AES_256-HMAC_SHA2_256 NATOA=none NATD=137.117.216.139:4500 DPD=none}
    May 13 15:09:30 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #68: the peer proposed: 192.168.29.0/24:0/0 -> 10.1.0.0/16:0/0
    May 13 15:09:30 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #204: responding to Quick Mode proposal {msgid:09000000}
    May 13 15:09:30 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #204:     us: 172.16.0.0/24===172.16.0.215---172.16.0.1
    May 13 15:09:30 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #204:   them: 137.117.216.139<137.117.216.139>===10.1.254.0/24
    May 13 15:09:30 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #204: keeping refhim=4294901761 during rekey
    May 13 15:09:30 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #204: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
    May 13 15:09:30 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #204: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
    May 13 15:09:30 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #204: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
    May 13 15:09:30 ip-172-16-0-215 pluto[26141]: "amznazure/1x0" #204: STATE_QUICK_R2: IPsec SA established tunnel mode {ESP=>0xb6d299cc <0xfd3f707f xfrm=AES_256-HMAC_SHA2_256 NATOA=none NATD=137.117.216.139:4500 DPD=none}
    May 13 15:09:39 ip-172-16-0-215 pluto[26141]: "amzncapbreton/8x0" #199: max number of retransmissions (2) reached STATE_QUICK_I1.  No acceptable response to our first Quick Mode message: perhaps peer likes no proposal
    May 13 15:09:39 ip-172-16-0-215 pluto[26141]: "amzncapbreton/8x0" #199: starting keying attempt 50 of an unlimited number
    May 13 15:11:59 ip-172-16-0-215 pluto[26141]: "amzncapbreton/8x0" #208: initiating Quick Mode PSK+ENCRYPT+TUNNEL+PFS+UP+IKEv2ALLOW+SAREFTRACK to replace #206 {using isakmp#3 msgid:85e04333 proposal=AES(12)_128-SHA1(2)_160 pfsgroup=OAKLEY_GROUP_MODP1024}



```Can you help me to avoid those disconnections ?


Thanks a lot !

---

### Post by slickymaster on 2014-05-13
Hi Zenwo, welcome to the forums.

I'm moving your thread to the **Networking & Wireless** sub-forum where you'll be able to get the proper and adequate help to your problem.

---

### Post by Zenwo on 2014-05-13
allright ;)

---

### Post by Zenwo on 2014-05-15
[COLOR=#444444][FONT=Arial]Problem solved by modifing the openswan to azure .conf : 

> 

conn amznazure
        authby=secret
        auto=start
        type=tunnel
        left=%defaultroute
        leftsubnets=172.16.0.0/24,192.168.16.0/24,192.168.31.0/24,192.168.29.0/24,192.168.13.0/24,192.168.30.0/24,192.168.11.0/24,192.168.33.0/24
        leftnexthop=%defaultroute
        right=137.117.216.139
        rightsubnet=10.1.254.0/24
        ike=aes128-sha1-modp1024
        esp=aes128-sha1
        pfs=no
        ikelifetime=8h
        keylife=1h



[/FONT][/COLOR]

---

