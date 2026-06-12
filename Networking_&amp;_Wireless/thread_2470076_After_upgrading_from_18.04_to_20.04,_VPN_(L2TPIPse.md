---
title: "After upgrading from 18.04 to 20.04, VPN (L2TP/IPsec) connection has stopped working"
date: 2021-12-19
forum: Networking &amp; Wireless
---

### Post by nockdown on 2021-12-19
After upgrading from 18.04 to 20.04, the VPN (L2TP/IPsec) connection has stopped working from home to pfSense 2.5.2.
IPsec settings on pfSense:
```
Key Exchange version - IKEv1
Internet Protocol - IPv4
Phase 1 Proposal (Authentication) Authentication Method - Matual PSK
Phase 1 Proposal (Authentication) Negotiation mode - Main
first:
Phase 1 Proposal (Encryption Algorithm) Encryption Algorithm - Algorithm - AES
Phase 1 Proposal (Encryption Algorithm) Encryption Algorithm - Key length - 256 bits
Phase 1 Proposal (Encryption Algorithm) Encryption Algorithm - Hash - SHA1
Phase 1 Proposal (Encryption Algorithm) Encryption Algorithm - DH Group - 14 (2048 bits)
second:
Phase 1 Proposal (Encryption Algorithm) Encryption Algorithm - Algorithm - AES
Phase 1 Proposal (Encryption Algorithm) Encryption Algorithm - Key length - 128 bits
Phase 1 Proposal (Encryption Algorithm) Encryption Algorithm - Hash - SHA1
Phase 1 Proposal (Encryption Algorithm) Encryption Algorithm - DH Group - 2 (1024 bits)
```


IKEv1 algorithms offered by the VPN server:
```
sudo ./ike-scan.sh XXX.XXX.XXX.XXX | grep SA=
SA=(Enc=AES KeyLength=128 Hash=SHA1 Group=2:modp1024 Auth=PSK LifeType=Seconds LifeDuration=28800)
SA=(Enc=AES KeyLength=128 Hash=SHA1 Group=2:modp1024 Auth=RSA_Sig LifeType=Seconds LifeDuration=28800)
SA=(Enc=AES KeyLength=256 Hash=SHA1 Group=14:modp2048 Auth=PSK LifeType=Seconds LifeDuration=28800)
SA=(Enc=AES KeyLength=256 Hash=SHA1 Group=14:modp2048 Auth=RSA_Sig LifeType=Seconds LifeDuration=28800)
```




Home settings:
```
Gateway: gate.xxx.ru
User name: login
Password: password
Enable IPsec tunnel to L2TP host - the jackdaw is
Pre-shared Key - secret
Phase1 algorithms: empty
Phase2 algorithms is empty
Enforce UDP encapsulation - the jackdaw stands
```


Home system:
```
Distributor ID: Ubuntu
Description: Ubuntu 20.04.3 LTS
Release: 20.04
Codename: focal
```


Installed:
```
libreswan 3.29-2build1
network-manager-l2tp 1.2.16-1
```


Checking the implementation that IPsec uses
```
ipsec --version
Linux Libreswan v4.5-769-g0427fd2bc6-main (XFRM) on 5.4.0-91-generic
```


NetworkManager journal
```
journalctl -u NetworkManager.service
```
```
NetworkManager[985]: <info> [1639930984.4586] audit: op="statistics" arg="refresh-rate-ms" pid=1575 uid=1000 result="success"
NetworkManager[985]: <info> [1639930985.6551] audit: op="connection-activate" uuid="4bcada90-93e5-4afa-9e11-1c3aec8e1937" name="speech" pid=1575 uid=1000 result="success"
NetworkManager[985]: <info> [1639930985.6580] vpn-connection[0x55b189866570,4bcada90-93e5-4afa-9e11-1c3aec8e1937,"speech",0]: Started the VPN service, PID 44306
NetworkManager[985]: <info> [1639930985.6630] vpn-connection[0x55b189866570,4bcada90-93e5-4afa-9e11-1c3aec8e1937,"speech",0]: Saw the service appear; activating connection
nm-l2tp-service[44306]: Check port 1701
nm-l2tp-service[44306]: Can't bind to port 1701
NetworkManager[44317]: Redirecting to: systemctl restart ipsec.service
NetworkManager[44636]: 002 listening for IKE messages
NetworkManager[44636]: 002 forgetting secrets
NetworkManager[44636]: 002 loading secrets from "/etc/ipsec.secrets"
NetworkManager[44636]: 002 loading secrets from "/etc/ipsec.d/ipsec.nm-l2tp.secrets"
NetworkManager[44641]: debugging mode enabled
NetworkManager[44641]: end of file /run/nm-l2tp-4bcada90-93e5-4afa-9e11-1c3aec8e1937/ipsec.conf
NetworkManager[44641]: Loading conn 4bcada90-93e5-4afa-9e11-1c3aec8e1937
NetworkManager[44641]: starter: left is KH_DEFAULTROUTE
NetworkManager[44641]: conn: "4bcada90-93e5-4afa-9e11-1c3aec8e1937" modecfgdns=<unset>
NetworkManager[44641]: conn: "4bcada90-93e5-4afa-9e11-1c3aec8e1937" modecfgdomains=<unset>
NetworkManager[44641]: conn: "4bcada90-93e5-4afa-9e11-1c3aec8e1937" modecfgbanner=<unset>
NetworkManager[44641]: conn: "4bcada90-93e5-4afa-9e11-1c3aec8e1937" mark=<unset>
NetworkManager[44641]: conn: "4bcada90-93e5-4afa-9e11-1c3aec8e1937" mark-in=<unset>
NetworkManager[44641]: conn: "4bcada90-93e5-4afa-9e11-1c3aec8e1937" mark-out=<unset>
NetworkManager[44641]: conn: "4bcada90-93e5-4afa-9e11-1c3aec8e1937" vti_iface=<unset>
NetworkManager[44641]: conn: "4bcada90-93e5-4afa-9e11-1c3aec8e1937" redirect-to=<unset>
NetworkManager[44641]: conn: "4bcada90-93e5-4afa-9e11-1c3aec8e1937" accept-redirect-to=<unset>
NetworkManager[44641]: conn: "4bcada90-93e5-4afa-9e11-1c3aec8e1937" esp=aes256-sha1,aes128-sha1,3des-sha1
NetworkManager[44641]: conn: "4bcada90-93e5-4afa-9e11-1c3aec8e1937" ike=aes256-sha2_256-modp2048,aes256-sha2_256-modp1536,aes256-sha2_256-modp1024,aes256-sha1-modp2048,aes256-sha1-modp1536,aes256-sha1-modp1024,aes256-sha1-ecp_384,aes128-sha1-modp1024,aes128-sha1-ecp>
NetworkManager[44641]: opening file: /run/nm-l2tp-4bcada90-93e5-4afa-9e11-1c3aec8e1937/ipsec.conf
NetworkManager[44641]: loading named conns: 4bcada90-93e5-4afa-9e11-1c3aec8e1937
NetworkManager[44641]: seeking_src = 1, seeking_gateway = 1, has_peer = 1
NetworkManager[44641]: seeking_src = 0, seeking_gateway = 1, has_dst = 1
NetworkManager[44641]: dst via 192.168.1.1 dev enp39s0 src table 254
NetworkManager[44641]: set nexthop: 192.168.1.1
NetworkManager[44641]: dst 169.254.0.0 via dev enp39s0 src table 254
NetworkManager[44641]: dst 192.168.0.0 via dev enp39s0 src 192.168.100.5 table 254
NetworkManager[44641]: dst 127.0.0.0 via dev lo src 127.0.0.1 table 255 (ignored)
NetworkManager[44641]: dst 127.0.0.0 via dev lo src 127.0.0.1 table 255 (ignored)
NetworkManager[44641]: dst 127.0.0.1 via dev lo src 127.0.0.1 table 255 (ignored)
NetworkManager[44641]: dst 127.255.255.255 via dev lo src 127.0.0.1 table 255 (ignored)
NetworkManager[44641]: dst 192.168.0.0 via dev enp39s0 src 192.168.100.5 table 255 (ignored)
NetworkManager[44641]: dst 192.168.100.5 via dev enp39s0 src 192.168.100.5 table 255 (ignored)
NetworkManager[44641]: dst 192.168.255.255 via dev enp39s0 src 192.168.100.5 table 255 (ignored)
NetworkManager[44641]: seeking_src = 1, seeking_gateway = 0, has_peer = 1
NetworkManager[44641]: seeking_src = 1, seeking_gateway = 0, has_dst = 1
NetworkManager[44641]: dst 192.168.1.1 via dev enp39s0 src 192.168.100.5 table 254
NetworkManager[44641]: set addr: 192.168.100.5
NetworkManager[44641]: seeking_src = 0, seeking_gateway = 0, has_peer = 1
NetworkManager[44643]: 002 "4bcada90-93e5-4afa-9e11-1c3aec8e1937" #1: initiating Main Mode
NetworkManager[44643]: 104 "4bcada90-93e5-4afa-9e11-1c3aec8e1937" #1: STATE_MAIN_I1: initiate
NetworkManager[44643]: 002 "4bcada90-93e5-4afa-9e11-1c3aec8e1937" #1: WARNING: connection 4bcada90-93e5-4afa-9e11-1c3aec8e1937 PSK length of 8 bytes is too short for sha PRF in FIPS mode (10 bytes required)
NetworkManager[44643]: 106 "4bcada90-93e5-4afa-9e11-1c3aec8e1937" #1: STATE_MAIN_I2: sent MI2, expecting MR2
NetworkManager[44643]: 108 "4bcada90-93e5-4afa-9e11-1c3aec8e1937" #1: STATE_MAIN_I3: sent MI3, expecting MR3
NetworkManager[44643]: 002 "4bcada90-93e5-4afa-9e11-1c3aec8e1937" #1: Peer ID is ID_IPV4_ADDR: 'XXX.XXX.XXX.XXX'
NetworkManager[44643]: 004 "4bcada90-93e5-4afa-9e11-1c3aec8e1937" #1: STATE_MAIN_I4: ISAKMP SA established {auth=PRESHARED_KEY cipher=AES_CBC_256 integ=HMAC_SHA1 group=MODP2048}
NetworkManager[44643]: 002 "4bcada90-93e5-4afa-9e11-1c3aec8e1937" #2: initiating Quick Mode PSK+ENCRYPT+PFS+UP+IKEV1_ALLOW+SAREF_TRACK+IKE_FRAG_ALLOW+ESN_NO {using isakmp#1 msgid:5b192655 proposal=AES_CBC_256-HMAC_SHA1_96, AES_CBC_128-HMAC_SHA1_96, 3DES_CBC-HMAC_SHA>
NetworkManager[44643]: 117 "4bcada90-93e5-4afa-9e11-1c3aec8e1937" #2: STATE_QUICK_I1: initiate
NetworkManager[44643]: 010 "4bcada90-93e5-4afa-9e11-1c3aec8e1937" #2: STATE_QUICK_I1: retransmission; will wait 0.5 seconds for response
NetworkManager[44643]: 010 "4bcada90-93e5-4afa-9e11-1c3aec8e1937" #2: STATE_QUICK_I1: retransmission; will wait 1 seconds for response
NetworkManager[44643]: 010 "4bcada90-93e5-4afa-9e11-1c3aec8e1937" #2: STATE_QUICK_I1: retransmission; will wait 2 seconds for response
NetworkManager[44643]: 010 "4bcada90-93e5-4afa-9e11-1c3aec8e1937" #2: STATE_QUICK_I1: retransmission; will wait 4 seconds for response
NetworkManager[44643]: 010 "4bcada90-93e5-4afa-9e11-1c3aec8e1937" #2: STATE_QUICK_I1: retransmission; will wait 8 seconds for response
nm-l2tp-service[44306]: g_dbus_method_invocation_take_error: assertion 'error != NULL' failed
NetworkManager[985]: <info> [1639930996.0948] vpn-connection[0x55b189866570,4bcada90-93e5-4afa-9e11-1c3aec8e1937,"speech",0]: VPN plugin: state changed: stopped (6)
NetworkManager[985]: <info> [1639930996.0971] vpn-connection[0x55b189866570,4bcada90-93e5-4afa-9e11-1c3aec8e1937,"speech",0]: VPN service disappeared
NetworkManager[985]: <warn> [1639930996.0982] vpn-connection[0x55b189866570,4bcada90-93e5-4afa-9e11-1c3aec8e1937,"speech",0]: VPN connection: failed to connect: 'Message recipient disconnected from message bus without replying'
NetworkManager[985]: <info> [1639930999.1694] audit: op="statistics" arg="refresh-rate-ms" pid=1575 uid=1000 result="success"
NetworkManager[44643]: 010 "4bcada90-93e5-4afa-9e11-1c3aec8e1937" #2: STATE_QUICK_I1: retransmission; will wait 16 seconds for response
NetworkManager[44643]: 010 "4bcada90-93e5-4afa-9e11-1c3aec8e1937" #2: STATE_QUICK_I1: retransmission; will wait 32 seconds for response
NetworkManager[44643]: 031 "4bcada90-93e5-4afa-9e11-1c3aec8e1937" #2: STATE_QUICK_I1: 60 second timeout exceeded after 7 retransmits. No acceptable response to our first Quick Mode message: perhaps peer likes no proposal
NetworkManager[44643]: 000 "4bcada90-93e5-4afa-9e11-1c3aec8e1937" #2: starting keying attempt 2 of an unlimited number, but releasing whack
```


As I understand, in Libreswan version 3.30 (February 13, 2020), DH2/modp1024 support is disabled during compilation. Ubuntu 20.04 was the last release that included Libreswan 3.29.
**Please, why my VPN connection has stopped working?**

---

### Post by dkosovic on 2022-01-03
From the NetworkManager-L2tp logs, main mode (I.e. phase 1) is successful, but quick mode (I.e. phase 2) is not. You posted the configuration details for phase 1, but don’t see them for phase 2. I suspect PFS wasn’t enabled for phase 2, so try disabling PFS in the IPsec configuration of NetworkManager-l2tp.

---

