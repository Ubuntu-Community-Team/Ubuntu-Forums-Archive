---
title: "L2TP problem connecting to VPN service: Invalid HASH_V1 payload length"
date: 2022-12-27
forum: Networking &amp; Wireless
---

### Post by trasan on 2022-12-27
Hi,

I keep getting these error when trying to connect from my remote (ubuntu) computer to home USG VPN service (L2TP):
Dec 27 20:36:25 kullen NetworkManager[1032]: invalid HASH_V1 payload length, decryption failed?Dec 27 20:36:25 kullen NetworkManager[1032]: could not decrypt payloads
Dec 27 20:36:25 kullen NetworkManager[1032]: message parsing failed

Cannot find any clear reason to why or how to solve it. Any hints?


Full log:
Dec 27 22:35:16 kullen NetworkManager[1032]: <info>  [1672176916.4742] audit: op="connection-activate" uuid="878bdef4-0219-429a-9f3d-50e80f95623e" name="VPN-HAR5" pid=8468 uid=1000 result="success"
Dec 27 22:35:16 kullen NetworkManager[1032]: <info>  [1672176916.4820] vpn-connection[0x5559c897a320,878bdef4-0219-429a-9f3d-50e80f95623e,"VPN-HAR5",0]: Started the VPN service, PID 8474
Dec 27 22:35:16 kullen NetworkManager[1032]: <info>  [1672176916.4891] vpn-connection[0x5559c897a320,878bdef4-0219-429a-9f3d-50e80f95623e,"VPN-HAR5",0]: Saw the service appear; activating connection
Dec 27 22:35:16 kullen NetworkManager[1032]: <info>  [1672176916.4958] vpn-connection[0x5559c897a320,878bdef4-0219-429a-9f3d-50e80f95623e,"VPN-HAR5",0]: VPN connection: (ConnectInteractive) reply received
Dec 27 22:35:16 kullen nm-l2tp-service[8474]: Check port 1701
Dec 27 22:35:16 kullen nm-l2tp-service[8474]: Can't bind to port 1701
Dec 27 22:35:16 kullen NetworkManager[1032]: Stopping strongSwan IPsec failed: starter is not running
Dec 27 22:35:18 kullen NetworkManager[1032]: Starting strongSwan 5.6.2 IPsec [starter]...
Dec 27 22:35:18 kullen NetworkManager[1032]: Loading config setup
Dec 27 22:35:18 kullen NetworkManager[1032]: Loading conn '878bdef4-0219-429a-9f3d-50e80f95623e'
Dec 27 22:35:18 kullen NetworkManager[1032]: found netkey IPsec stack
Dec 27 22:35:18 kullen charon: 00[DMN] Starting IKE charon daemon (strongSwan 5.6.2, Linux 4.15.0-200-generic, x86_64)
Dec 27 22:35:18 kullen charon: 00[CFG] loading ca certificates from '/etc/ipsec.d/cacerts'
Dec 27 22:35:18 kullen charon: 00[CFG] loading aa certificates from '/etc/ipsec.d/aacerts'
Dec 27 22:35:18 kullen charon: 00[CFG] loading ocsp signer certificates from '/etc/ipsec.d/ocspcerts'
Dec 27 22:35:18 kullen charon: 00[CFG] loading attribute certificates from '/etc/ipsec.d/acerts'
Dec 27 22:35:18 kullen charon: 00[CFG] loading crls from '/etc/ipsec.d/crls'
Dec 27 22:35:18 kullen charon: 00[CFG] loading secrets from '/etc/ipsec.secrets'
Dec 27 22:35:18 kullen charon: 00[CFG] loading secrets from '/etc/ipsec.d/ipsec.nm-l2tp.secrets'
Dec 27 22:35:18 kullen charon: 00[CFG]   loaded IKE secret for %any
Dec 27 22:35:18 kullen charon: 00[CFG] loading secrets from '/etc/ipsec.d/ipsec.nm-l2tp.secrets'
Dec 27 22:35:18 kullen charon: 00[CFG]   loaded IKE secret for %any
Dec 27 22:35:18 kullen charon: 00[LIB] loaded plugins: charon aesni aes rc2 sha2 sha1 md4 md5 mgf1 random nonce x509 revocation constraints pubkey pkcs1 pkcs7 pkcs8 pkcs12 pgp dnskey sshkey pem openssl fips-prf gmp agent xcbc hmac gcm attr kernel-netlink resolve socket-default connmark stroke updown eap-mschapv2 xauth-generic counters
Dec 27 22:35:18 kullen charon: 00[LIB] dropped capabilities, running as uid 0, gid 0
Dec 27 22:35:18 kullen charon: 00[JOB] spawning 16 worker threads
Dec 27 22:35:18 kullen charon: 06[CFG] received stroke: add connection '878bdef4-0219-429a-9f3d-50e80f95623e'
Dec 27 22:35:18 kullen charon: 06[CFG] added configuration '878bdef4-0219-429a-9f3d-50e80f95623e'
Dec 27 22:35:19 kullen charon: 08[CFG] rereading secrets
Dec 27 22:35:19 kullen charon: 08[CFG] loading secrets from '/etc/ipsec.secrets'
Dec 27 22:35:19 kullen charon: 08[CFG] loading secrets from '/etc/ipsec.d/ipsec.nm-l2tp.secrets'
Dec 27 22:35:19 kullen charon: 08[CFG]   loaded IKE secret for %any
Dec 27 22:35:19 kullen charon: 08[CFG] loading secrets from '/etc/ipsec.d/ipsec.nm-l2tp.secrets'
Dec 27 22:35:19 kullen charon: 08[CFG]   loaded IKE secret for %any
Dec 27 22:35:19 kullen charon: 09[CFG] received stroke: initiate '878bdef4-0219-429a-9f3d-50e80f95623e'
Dec 27 22:35:19 kullen charon: 11[IKE] initiating Main Mode IKE_SA 878bdef4-0219-429a-9f3d-50e80f95623e[1] to <REMOTE IP>
Dec 27 22:35:19 kullen charon: 11[ENC] generating ID_PROT request 0 [ SA V V V V V ]
Dec 27 22:35:19 kullen charon: 11[NET] sending packet: from 192.168.40.10[500] to <REMOTE IP>[500] (532 bytes)
Dec 27 22:35:19 kullen charon: 12[NET] received packet: from <REMOTE IP>[500] to 192.168.40.10[500] (136 bytes)
Dec 27 22:35:19 kullen charon: 12[ENC] parsed ID_PROT response 0 [ SA V V V ]
Dec 27 22:35:19 kullen charon: 12[IKE] received XAuth vendor ID
Dec 27 22:35:19 kullen charon: 12[IKE] received DPD vendor ID
Dec 27 22:35:19 kullen charon: 12[IKE] received NAT-T (RFC 3947) vendor ID
Dec 27 22:35:19 kullen charon: 12[ENC] generating ID_PROT request 0 [ KE No NAT-D NAT-D ]
Dec 27 22:35:19 kullen charon: 12[NET] sending packet: from 192.168.40.10[500] to <REMOTE IP>[500] (372 bytes)
Dec 27 22:35:20 kullen charon: 13[NET] received packet: from <REMOTE IP>[500] to 192.168.40.10[500] (372 bytes)
Dec 27 22:35:20 kullen charon: 13[ENC] parsed ID_PROT response 0 [ KE No NAT-D NAT-D ]
Dec 27 22:35:20 kullen charon: 13[IKE] local host is behind NAT, sending keep alives
Dec 27 22:35:20 kullen charon: 13[ENC] generating ID_PROT request 0 [ ID HASH ]
Dec 27 22:35:20 kullen charon: 13[NET] sending packet: from 192.168.40.10[4500] to <REMOTE IP>[4500] (76 bytes)
Dec 27 22:35:20 kullen charon: 14[NET] received packet: from <REMOTE IP>[500] to 192.168.40.10[500] (76 bytes)
Dec 27 22:35:20 kullen charon: 14[ENC] invalid HASH_V1 payload length, decryption failed?
Dec 27 22:35:20 kullen charon: 14[ENC] could not decrypt payloads
Dec 27 22:35:20 kullen charon: 14[IKE] message parsing failed
Dec 27 22:35:20 kullen charon: 14[IKE] ignore malformed INFORMATIONAL request
Dec 27 22:35:20 kullen charon: 14[IKE] INFORMATIONAL_V1 request with message ID 3723659419 processing failed
Dec 27 22:35:24 kullen charon: 05[IKE] sending retransmit 1 of request message ID 0, seq 3
Dec 27 22:35:24 kullen charon: 05[NET] sending packet: from 192.168.40.10[4500] to <REMOTE IP>[4500] (76 bytes)
Dec 27 22:35:24 kullen charon: 06[NET] received packet: from <REMOTE IP>[500] to 192.168.40.10[500] (76 bytes)
Dec 27 22:35:24 kullen charon: 06[ENC] invalid HASH_V1 payload length, decryption failed?
Dec 27 22:35:24 kullen charon: 06[ENC] could not decrypt payloads
Dec 27 22:35:24 kullen charon: 06[IKE] message parsing failed
Dec 27 22:35:24 kullen charon: 06[IKE] ignore malformed INFORMATIONAL request
Dec 27 22:35:24 kullen charon: 06[IKE] INFORMATIONAL_V1 request with message ID 1388887596 processing failed
Dec 27 22:35:29 kullen NetworkManager[1032]: Stopping strongSwan IPsec...
Dec 27 22:35:29 kullen charon: 00[DMN] signal of type SIGINT received. Shutting down
Dec 27 22:35:29 kullen charon: 00[IKE] destroying IKE_SA in state CONNECTING without notification
Dec 27 22:35:29 kullen NetworkManager[1032]: initiating Main Mode IKE_SA 878bdef4-0219-429a-9f3d-50e80f95623e[1] to <REMOTE IP>
Dec 27 22:35:29 kullen NetworkManager[1032]: generating ID_PROT request 0 [ SA V V V V V ]
Dec 27 22:35:29 kullen NetworkManager[1032]: sending packet: from 192.168.40.10[500] to <REMOTE IP>[500] (532 bytes)
Dec 27 22:35:29 kullen NetworkManager[1032]: received packet: from <REMOTE IP>[500] to 192.168.40.10[500] (136 bytes)
Dec 27 22:35:29 kullen NetworkManager[1032]: parsed ID_PROT response 0 [ SA V V V ]
Dec 27 22:35:29 kullen NetworkManager[1032]: received XAuth vendor ID
Dec 27 22:35:29 kullen NetworkManager[1032]: received DPD vendor ID
Dec 27 22:35:29 kullen NetworkManager[1032]: received NAT-T (RFC 3947) vendor ID
Dec 27 22:35:29 kullen NetworkManager[1032]: generating ID_PROT request 0 [ KE No NAT-D NAT-D ]
Dec 27 22:35:29 kullen NetworkManager[1032]: sending packet: from 192.168.40.10[500] to <REMOTE IP>[500] (372 bytes)
Dec 27 22:35:29 kullen NetworkManager[1032]: received packet: from <REMOTE IP>[500] to 192.168.40.10[500] (372 bytes)
Dec 27 22:35:29 kullen NetworkManager[1032]: parsed ID_PROT response 0 [ KE No NAT-D NAT-D ]
Dec 27 22:35:29 kullen NetworkManager[1032]: local host is behind NAT, sending keep alives
Dec 27 22:35:29 kullen NetworkManager[1032]: generating ID_PROT request 0 [ ID HASH ]
Dec 27 22:35:29 kullen NetworkManager[1032]: sending packet: from 192.168.40.10[4500] to <REMOTE IP>[4500] (76 bytes)
Dec 27 22:35:29 kullen NetworkManager[1032]: received packet: from <REMOTE IP>[500] to 192.168.40.10[500] (76 bytes)
Dec 27 22:35:29 kullen NetworkManager[1032]: invalid HASH_V1 payload length, decryption failed?
Dec 27 22:35:29 kullen NetworkManager[1032]: could not decrypt payloads
Dec 27 22:35:29 kullen NetworkManager[1032]: message parsing failed
Dec 27 22:35:29 kullen NetworkManager[1032]: ignore malformed INFORMATIONAL request
Dec 27 22:35:29 kullen NetworkManager[1032]: INFORMATIONAL_V1 request with message ID 3723659419 processing failed
Dec 27 22:35:29 kullen NetworkManager[1032]: sending retransmit 1 of request message ID 0, seq 3
Dec 27 22:35:29 kullen NetworkManager[1032]: sending packet: from 192.168.40.10[4500] to <REMOTE IP>[4500] (76 bytes)
Dec 27 22:35:29 kullen NetworkManager[1032]: received packet: from <REMOTE IP>[500] to 192.168.40.10[500] (76 bytes)
Dec 27 22:35:29 kullen NetworkManager[1032]: invalid HASH_V1 payload length, decryption failed?
Dec 27 22:35:29 kullen NetworkManager[1032]: could not decrypt payloads
Dec 27 22:35:29 kullen NetworkManager[1032]: message parsing failed
Dec 27 22:35:29 kullen NetworkManager[1032]: ignore malformed INFORMATIONAL request
Dec 27 22:35:29 kullen NetworkManager[1032]: INFORMATIONAL_V1 request with message ID 1388887596 processing failed
Dec 27 22:35:29 kullen NetworkManager[1032]: destroying IKE_SA in state CONNECTING without notification
Dec 27 22:35:29 kullen NetworkManager[1032]: establishing connection '878bdef4-0219-429a-9f3d-50e80f95623e' failed
Dec 27 22:35:29 kullen nm-l2tp-service[8474]: Could not establish IPsec connection.
Dec 27 22:35:29 kullen nm-l2tp-service[8474]: g_dbus_method_invocation_take_error: assertion 'error != NULL' failed
Dec 27 22:35:29 kullen NetworkManager[1032]: <info>  [1672176929.6785] vpn-connection[0x5559c897a320,878bdef4-0219-429a-9f3d-50e80f95623e,"VPN-HAR5",0]: VPN plugin: state changed: stopped (6)
Dec 27 22:35:29 kullen NetworkManager[1032]: <info>  [1672176929.6835] vpn-connection[0x5559c897a320,878bdef4-0219-429a-9f3d-50e80f95623e,"VPN-HAR5",0]: VPN service disappeared
Dec 27 22:35:29 kullen NetworkManager[1032]: <warn>  [1672176929.6848] vpn-connection[0x5559c897a320,878bdef4-0219-429a-9f3d-50e80f95623e,"VPN-HAR5",0]: VPN connection: failed to connect: 'Message recipient disconnected from message bus without replying'

---

### Post by dkosovic on 2022-12-29
Probably some sort of compatibility issue between the older version of strongswan on the USG compared to the version that comes with Ubuntu 22.04.

You could try increasing [SIZE=1][FONT=courier new]charon.max_ikev1_exchanges[/FONT][/SIZE] in the [SIZE=1][FONT=courier new]/etc/strongswan.conf[/FONT][/SIZE] file as the log seems to indicate it is failing after 3 Main Mode exchanges.

Alternatively you could try switching to libreswan with the following and see if that makes a difference:

```
sudo apt install libreswan
```

---

### Post by trasan on 2022-12-31
thanks, tried both but did not make any difference.

---

### Post by dkosovic on 2023-01-02
The issue is occurring in Main Mode (aka phase 1), perhaps the USG can't handle the stronger algorithms in the proposals network-manager-l2tp is sending. Perhaps some of those algorithms are unknown to the USG and it is barfing instead of providing a no proposal selected error message. Maybe something in the logs on the USG.

You'll need to switch back to strongswan as libreswan no longer handles the really weak MOD1024 proposal that Win10 uses and presumably the USG. Use "[SIZE=1][FONT=courier new]sudo apt install strongswan"[/FONT][/SIZE] to revert to strongswan.

In the IPsec configuration dialog, use the following settings:
  **Phase 1 Algorithms:** 3des-sha1-modp1024!
  **Phase 2 Algorithms:** 3des-sha1![COLOR=#24292F][FONT=ui-monospace]

[/FONT][/COLOR]Note the exclamation mark (!) is required with strongswan to override the existing settings, rather than append.

Actually looks like someone has used those Phase 1 and Phase 2 settings with network-manager-l2tp and a USG :
[https://community.ui.com/questions/Create-VPN-connection-to-Unifi-USG-from-Ubuntu-Linux-Client-using-Network-Manager-Graphically/27e65f9e-169b-4a7f-9bc8-3304b571f6e2](https://community.ui.com/questions/Create-VPN-connection-to-Unifi-USG-from-Ubuntu-Linux-Client-using-Network-Manager-Graphically/27e65f9e-169b-4a7f-9bc8-3304b571f6e2)

---

### Post by trasan on 2023-01-03
Thanks dkosovic, it help. Now working as expected. I think it was the change of the Phase 1 and 2 that did it.

---

