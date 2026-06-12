---
title: "Unable to connect to L2TP/IPSec VPN via NM and xl2tp"
date: 2021-03-02
forum: Networking &amp; Wireless
---

### Post by trevorsears on 2021-03-02
I have been to troubleshoot all morning as to how to get connected to my employer's VPN via Network Manager. I found a number of support threads on various sites and have tried all of what was suggested, as well as mixes of solutions, and nothing has worked.

First off, here's the log from Network Manager after attempting to connect to the VPN through the GUI:

```
$ journalctl -u NetworkManager | tail -n 200 | less
Mar 02 10:19:15 xps NetworkManager[5170]: Starting strongSwan 5.8.2 IPsec [starter]...
Mar 02 10:19:15 xps NetworkManager[5170]: Loading config setup
Mar 02 10:19:15 xps NetworkManager[5170]: Loading conn 'e30e20a1-6f99-46d8-9e7e-2007356cff21'
Mar 02 10:19:15 xps ipsec_starter[5170]: Starting strongSwan 5.8.2 IPsec [starter]...
Mar 02 10:19:15 xps ipsec_starter[5170]: Loading config setup
Mar 02 10:19:15 xps ipsec_starter[5170]: Loading conn 'e30e20a1-6f99-46d8-9e7e-2007356cff21'
Mar 02 10:19:15 xps ipsec_starter[5221]: Attempting to start charon...
Mar 02 10:19:15 xps charon[5222]: 00[DMN] Starting IKE charon daemon (strongSwan 5.8.2, Linux 5.8.0-44-generic, x86_64)
Mar 02 10:19:15 xps charon[5222]: 00[CFG] loading ca certificates from '/etc/ipsec.d/cacerts'
Mar 02 10:19:15 xps charon[5222]: 00[CFG] loading aa certificates from '/etc/ipsec.d/aacerts'
Mar 02 10:19:15 xps charon[5222]: 00[CFG] loading ocsp signer certificates from '/etc/ipsec.d/ocspcerts'
Mar 02 10:19:15 xps charon[5222]: 00[CFG] loading attribute certificates from '/etc/ipsec.d/acerts'
Mar 02 10:19:15 xps charon[5222]: 00[CFG] loading crls from '/etc/ipsec.d/crls'
Mar 02 10:19:15 xps charon[5222]: 00[CFG] loading secrets from '/etc/ipsec.secrets'
Mar 02 10:19:15 xps charon[5222]: 00[CFG] loading secrets from '/etc/ipsec.d/ipsec.nm-l2tp.secrets'
Mar 02 10:19:15 xps charon[5222]: 00[CFG]   loaded IKE secret for %any
Mar 02 10:19:15 xps charon[5222]: 00[LIB] loaded plugins: charon aesni aes rc2 sha2 sha1 md5 mgf1 random nonce x509 revocation constraints pubkey pkcs1 pkcs7 pkcs8 pkcs12 pgp dnskey sshkey pem openssl fips-prf gmp agent xcbc hmac gcm drbg attr kernel-netlink resolve socket-
default connmark stroke updown eap-mschapv2 xauth-generic counters
Mar 02 10:19:15 xps charon[5222]: 00[LIB] dropped capabilities, running as uid 0, gid 0
Mar 02 10:19:15 xps charon[5222]: 00[JOB] spawning 16 worker threads
Mar 02 10:19:15 xps ipsec_starter[5221]: charon (5222) started after 20 ms
Mar 02 10:19:15 xps charon[5222]: 05[CFG] received stroke: add connection 'e30e20a1-6f99-46d8-9e7e-2007356cff21'
Mar 02 10:19:15 xps charon[5222]: 05[CFG] added configuration 'e30e20a1-6f99-46d8-9e7e-2007356cff21'
Mar 02 10:19:16 xps charon[5222]: 10[CFG] rereading secrets
Mar 02 10:19:16 xps charon[5222]: 10[CFG] loading secrets from '/etc/ipsec.secrets'
Mar 02 10:19:16 xps charon[5222]: 10[CFG] loading secrets from '/etc/ipsec.d/ipsec.nm-l2tp.secrets'
Mar 02 10:19:16 xps charon[5222]: 10[CFG]   loaded IKE secret for %any
Mar 02 10:19:16 xps charon[5222]: 11[CFG] received stroke: initiate 'e30e20a1-6f99-46d8-9e7e-2007356cff21'
Mar 02 10:19:16 xps charon[5222]: 13[IKE] initiating Main Mode IKE_SA e30e20a1-6f99-46d8-9e7e-2007356cff21[1] to 71.89.153.210
Mar 02 10:19:16 xps charon[5222]: 13[IKE] initiating Main Mode IKE_SA e30e20a1-6f99-46d8-9e7e-2007356cff21[1] to 71.89.153.210
Mar 02 10:19:16 xps charon[5222]: 13[ENC] generating ID_PROT request 0 [ SA V V V V V ]
Mar 02 10:19:16 xps charon[5222]: 13[NET] sending packet: from 10.0.1.58[500] to 71.89.153.210[500] (532 bytes)
Mar 02 10:19:16 xps charon[5222]: 14[NET] received packet: from 71.89.153.210[500] to 10.0.1.58[500] (112 bytes)
Mar 02 10:19:16 xps charon[5222]: 14[ENC] parsed ID_PROT response 0 [ SA V V ]
Mar 02 10:19:16 xps charon[5222]: 14[ENC] received unknown vendor ID: 5b:36:2b:c8:20:f6:00:07
Mar 02 10:19:16 xps charon[5222]: 14[IKE] received NAT-T (RFC 3947) vendor ID
Mar 02 10:19:16 xps charon[5222]: 14[CFG] selected proposal: IKE:3DES_CBC/HMAC_SHA1_96/PRF_HMAC_SHA1/MODP_1024
Mar 02 10:19:16 xps charon[5222]: 14[ENC] generating ID_PROT request 0 [ KE No NAT-D NAT-D ]
Mar 02 10:19:16 xps charon[5222]: 14[NET] sending packet: from 10.0.1.58[500] to 71.89.153.210[500] (244 bytes)
Mar 02 10:19:16 xps charon[5222]: 01[NET] received packet: from 71.89.153.210[500] to 10.0.1.58[500] (276 bytes)
Mar 02 10:19:16 xps charon[5222]: 01[ENC] parsed ID_PROT response 0 [ KE NAT-D NAT-D No V V V ]
Mar 02 10:19:16 xps charon[5222]: 01[ENC] received unknown vendor ID: 40:4b:f4:39:52:2c:a3:f6
Mar 02 10:19:16 xps charon[5222]: 01[IKE] received XAuth vendor ID
Mar 02 10:19:16 xps charon[5222]: 01[IKE] received DPD vendor ID
Mar 02 10:19:16 xps charon[5222]: 01[IKE] local host is behind NAT, sending keep alives
Mar 02 10:19:16 xps charon[5222]: 01[ENC] generating ID_PROT request 0 [ ID HASH ]
Mar 02 10:19:16 xps charon[5222]: 01[NET] sending packet: from 10.0.1.58[4500] to 71.89.153.210[4500] (68 bytes)
Mar 02 10:19:16 xps charon[5222]: 06[NET] received packet: from 71.89.153.210[4500] to 10.0.1.58[4500] (76 bytes)
Mar 02 10:19:16 xps charon[5222]: 06[IKE] queueing TRANSACTION request as tasks still active
Mar 02 10:19:20 xps charon[5222]: 07[IKE] sending retransmit 1 of request message ID 0, seq 3
Mar 02 10:19:20 xps charon[5222]: 07[NET] sending packet: from 10.0.1.58[4500] to 71.89.153.210[4500] (68 bytes)
Mar 02 10:19:20 xps charon[5222]: 09[NET] received packet: from 71.89.153.210[4500] to 10.0.1.58[4500] (92 bytes)
Mar 02 10:19:20 xps charon[5222]: 09[ENC] payload type ID_V1 was not encrypted
Mar 02 10:19:20 xps charon[5222]: 09[ENC] could not decrypt payloads
Mar 02 10:19:20 xps charon[5222]: 09[IKE] integrity check failed
Mar 02 10:19:20 xps charon[5222]: 09[ENC] generating INFORMATIONAL_V1 request 65355755 [ HASH N(INVAL_HASH) ]
Mar 02 10:19:20 xps charon[5222]: 09[NET] sending packet: from 10.0.1.58[4500] to 71.89.153.210[4500] (68 bytes)
Mar 02 10:19:20 xps charon[5222]: 09[IKE] ID_PROT response with message ID 0 processing failed
Mar 02 10:19:26 xps NetworkManager[5273]: Stopping strongSwan IPsec...
Mar 02 10:19:26 xps charon[5222]: 00[DMN] signal of type SIGINT received. Shutting down
Mar 02 10:19:26 xps charon[5222]: 00[IKE] destroying IKE_SA in state CONNECTING without notification
Mar 02 10:19:26 xps NetworkManager[5252]: initiating Main Mode IKE_SA e30e20a1-6f99-46d8-9e7e-2007356cff21[1] to 71.89.153.210
Mar 02 10:19:26 xps NetworkManager[5252]: generating ID_PROT request 0 [ SA V V V V V ]
Mar 02 10:19:26 xps NetworkManager[5252]: sending packet: from 10.0.1.58[500] to 71.89.153.210[500] (532 bytes)
Mar 02 10:19:26 xps NetworkManager[5252]: received packet: from 71.89.153.210[500] to 10.0.1.58[500] (112 bytes)
Mar 02 10:19:26 xps NetworkManager[5252]: parsed ID_PROT response 0 [ SA V V ]
Mar 02 10:19:26 xps NetworkManager[5252]: received unknown vendor ID: 5b:36:2b:c8:20:f6:00:07
Mar 02 10:19:26 xps NetworkManager[5252]: received NAT-T (RFC 3947) vendor ID
Mar 02 10:19:26 xps NetworkManager[5252]: selected proposal: IKE:3DES_CBC/HMAC_SHA1_96/PRF_HMAC_SHA1/MODP_1024
Mar 02 10:19:26 xps NetworkManager[5252]: generating ID_PROT request 0 [ KE No NAT-D NAT-D ]
Mar 02 10:19:26 xps NetworkManager[5252]: sending packet: from 10.0.1.58[500] to 71.89.153.210[500] (244 bytes)
Mar 02 10:19:26 xps NetworkManager[5252]: received packet: from 71.89.153.210[500] to 10.0.1.58[500] (276 bytes)
Mar 02 10:19:26 xps NetworkManager[5252]: parsed ID_PROT response 0 [ KE NAT-D NAT-D No V V V ]
Mar 02 10:19:26 xps NetworkManager[5252]: received unknown vendor ID: 40:4b:f4:39:52:2c:a3:f6
Mar 02 10:19:26 xps NetworkManager[5252]: received XAuth vendor ID
Mar 02 10:19:26 xps NetworkManager[5252]: received DPD vendor ID
Mar 02 10:19:26 xps NetworkManager[5252]: local host is behind NAT, sending keep alives
Mar 02 10:19:26 xps NetworkManager[5252]: generating ID_PROT request 0 [ ID HASH ]
Mar 02 10:19:26 xps NetworkManager[5252]: sending packet: from 10.0.1.58[4500] to 71.89.153.210[4500] (68 bytes)
Mar 02 10:19:26 xps NetworkManager[5252]: received packet: from 71.89.153.210[4500] to 10.0.1.58[4500] (76 bytes)
Mar 02 10:19:26 xps NetworkManager[5252]: queueing TRANSACTION request as tasks still active
Mar 02 10:19:26 xps NetworkManager[5252]: sending retransmit 1 of request message ID 0, seq 3
Mar 02 10:19:26 xps NetworkManager[5252]: sending packet: from 10.0.1.58[4500] to 71.89.153.210[4500] (68 bytes)
Mar 02 10:19:26 xps NetworkManager[5252]: received packet: from 71.89.153.210[4500] to 10.0.1.58[4500] (92 bytes)
Mar 02 10:19:26 xps NetworkManager[5252]: payload type ID_V1 was not encrypted
Mar 02 10:19:26 xps NetworkManager[5252]: could not decrypt payloads
Mar 02 10:19:26 xps NetworkManager[5252]: integrity check failed
Mar 02 10:19:26 xps NetworkManager[5252]: generating INFORMATIONAL_V1 request 65355755 [ HASH N(INVAL_HASH) ]
Mar 02 10:19:26 xps NetworkManager[5252]: sending packet: from 10.0.1.58[4500] to 71.89.153.210[4500] (68 bytes)
Mar 02 10:19:26 xps NetworkManager[5252]: ID_PROT response with message ID 0 processing failed
Mar 02 10:19:26 xps NetworkManager[5252]: destroying IKE_SA in state CONNECTING without notification
Mar 02 10:19:26 xps NetworkManager[5252]: establishing connection 'e30e20a1-6f99-46d8-9e7e-2007356cff21' failed
Mar 02 10:19:26 xps ipsec_starter[5221]: child 5222 (charon) has quit (exit code 0)
Mar 02 10:19:26 xps ipsec_starter[5221]: 
Mar 02 10:19:26 xps ipsec_starter[5221]: charon stopped after 200 ms
Mar 02 10:19:26 xps ipsec_starter[5221]: ipsec starter stopped
Mar 02 10:19:26 xps nm-l2tp-service[5158]: g_dbus_method_invocation_take_error: assertion 'error != NULL' failed
Mar 02 10:19:26 xps NetworkManager[5096]: <info>  [1614698366.5234] vpn-connection[0x55d317c68100,e30e20a1-6f99-46d8-9e7e-2007356cff21,"Company",0]: VPN plugin: state changed: stopped (6)
Mar 02 10:19:26 xps NetworkManager[5096]: <info>  [1614698366.5249] manager: startup complete
Mar 02 10:19:26 xps NetworkManager[5096]: <info>  [1614698366.5266] vpn-connection[0x55d317c68100,e30e20a1-6f99-46d8-9e7e-2007356cff21,"Company",0]: VPN service disappeared
Mar 02 10:19:26 xps NetworkManager[5096]: <warn>  [1614698366.5282] vpn-connection[0x55d317c68100,e30e20a1-6f99-46d8-9e7e-2007356cff21,"Company",0]: VPN connection: failed to connect: 'Message recipient disconnected from message bus without replying'
```

One of the few modifications that seemed to have a positive effect was adding the following line to my strongswan conf (/etc/strongswan.conf):

```
accept_unencrypted_mainmode_messages = yes
```

Which seems to resolve the 'could not decrypt payloads' error, and results in the following log:

```
Mar 02 10:40:19 xps nm-l2tp-service[6195]: Check port 1701
Mar 02 10:40:19 xps NetworkManager[6210]: Stopping strongSwan IPsec failed: starter is not running
Mar 02 10:40:21 xps NetworkManager[6207]: Starting strongSwan 5.8.2 IPsec [starter]...
Mar 02 10:40:21 xps ipsec_starter[6207]: Starting strongSwan 5.8.2 IPsec [starter]...
Mar 02 10:40:21 xps NetworkManager[6207]: Loading config setup
Mar 02 10:40:21 xps NetworkManager[6207]: Loading conn 'e30e20a1-6f99-46d8-9e7e-2007356cff21'
Mar 02 10:40:21 xps ipsec_starter[6207]: Loading config setup
Mar 02 10:40:21 xps ipsec_starter[6207]: Loading conn 'e30e20a1-6f99-46d8-9e7e-2007356cff21'
Mar 02 10:40:21 xps ipsec_starter[6220]: Attempting to start charon...
Mar 02 10:40:21 xps charon[6221]: 00[DMN] Starting IKE charon daemon (strongSwan 5.8.2, Linux 5.8.0-44-generic, x86_64)
Mar 02 10:40:21 xps charon[6221]: 00[CFG] loading ca certificates from '/etc/ipsec.d/cacerts'
Mar 02 10:40:21 xps charon[6221]: 00[CFG] loading aa certificates from '/etc/ipsec.d/aacerts'
Mar 02 10:40:21 xps charon[6221]: 00[CFG] loading ocsp signer certificates from '/etc/ipsec.d/ocspcerts'
Mar 02 10:40:21 xps charon[6221]: 00[CFG] loading attribute certificates from '/etc/ipsec.d/acerts'
Mar 02 10:40:21 xps charon[6221]: 00[CFG] loading crls from '/etc/ipsec.d/crls'
Mar 02 10:40:21 xps charon[6221]: 00[CFG] loading secrets from '/etc/ipsec.secrets'
Mar 02 10:40:21 xps charon[6221]: 00[CFG] loading secrets from '/etc/ipsec.d/ipsec.nm-l2tp.secrets'
Mar 02 10:40:21 xps charon[6221]: 00[CFG]   loaded IKE secret for %any
Mar 02 10:40:21 xps charon[6221]: 00[LIB] loaded plugins: charon aesni aes rc2 sha2 sha1 md5 mgf1 random nonce x509 revocation constraints pubkey pkcs1 pkcs7 pkcs8 pkcs12 pgp dnskey sshkey pem openssl fips-prf gmp agent xcbc hmac gcm drbg attr kernel-netlink resolve socket-
default connmark stroke updown eap-mschapv2 xauth-generic counters
Mar 02 10:40:21 xps charon[6221]: 00[LIB] dropped capabilities, running as uid 0, gid 0
Mar 02 10:40:21 xps charon[6221]: 00[JOB] spawning 16 worker threads
Mar 02 10:40:21 xps ipsec_starter[6220]: charon (6221) started after 20 ms
Mar 02 10:40:21 xps charon[6221]: 06[CFG] received stroke: add connection 'e30e20a1-6f99-46d8-9e7e-2007356cff21'
Mar 02 10:40:21 xps charon[6221]: 06[CFG] added configuration 'e30e20a1-6f99-46d8-9e7e-2007356cff21'
Mar 02 10:40:22 xps charon[6221]: 07[CFG] rereading secrets
Mar 02 10:40:22 xps charon[6221]: 07[CFG] loading secrets from '/etc/ipsec.secrets'
Mar 02 10:40:22 xps charon[6221]: 07[CFG] loading secrets from '/etc/ipsec.d/ipsec.nm-l2tp.secrets'
Mar 02 10:40:22 xps charon[6221]: 07[CFG]   loaded IKE secret for %any
Mar 02 10:40:22 xps charon[6221]: 09[CFG] received stroke: initiate 'e30e20a1-6f99-46d8-9e7e-2007356cff21'
Mar 02 10:40:22 xps charon[6221]: 12[IKE] initiating Main Mode IKE_SA e30e20a1-6f99-46d8-9e7e-2007356cff21[1] to 71.89.153.210
Mar 02 10:40:22 xps charon[6221]: 12[IKE] initiating Main Mode IKE_SA e30e20a1-6f99-46d8-9e7e-2007356cff21[1] to 71.89.153.210
Mar 02 10:40:22 xps charon[6221]: 12[ENC] generating ID_PROT request 0 [ SA V V V V V ]
Mar 02 10:40:22 xps charon[6221]: 12[NET] sending packet: from 10.0.1.58[500] to 71.89.153.210[500] (532 bytes)
Mar 02 10:40:22 xps charon[6221]: 13[NET] received packet: from 71.89.153.210[500] to 10.0.1.58[500] (112 bytes)
Mar 02 10:40:22 xps charon[6221]: 13[ENC] parsed ID_PROT response 0 [ SA V V ]
Mar 02 10:40:22 xps charon[6221]: 13[ENC] received unknown vendor ID: 5b:36:2b:c8:20:f6:00:07
Mar 02 10:40:22 xps charon[6221]: 13[IKE] received NAT-T (RFC 3947) vendor ID
Mar 02 10:40:22 xps charon[6221]: 13[CFG] selected proposal: IKE:3DES_CBC/HMAC_SHA1_96/PRF_HMAC_SHA1/MODP_1024
Mar 02 10:40:22 xps charon[6221]: 13[ENC] generating ID_PROT request 0 [ KE No NAT-D NAT-D ]
Mar 02 10:40:22 xps charon[6221]: 13[NET] sending packet: from 10.0.1.58[500] to 71.89.153.210[500] (244 bytes)
Mar 02 10:40:22 xps charon[6221]: 14[NET] received packet: from 71.89.153.210[500] to 10.0.1.58[500] (276 bytes)
Mar 02 10:40:22 xps charon[6221]: 14[ENC] parsed ID_PROT response 0 [ KE NAT-D NAT-D No V V V ]
Mar 02 10:40:22 xps charon[6221]: 14[ENC] received unknown vendor ID: 40:4b:f4:39:52:2c:a3:f6
Mar 02 10:40:22 xps charon[6221]: 14[IKE] received XAuth vendor ID
Mar 02 10:40:22 xps charon[6221]: 14[IKE] received DPD vendor ID
Mar 02 10:40:22 xps charon[6221]: 14[IKE] local host is behind NAT, sending keep alives
Mar 02 10:40:22 xps charon[6221]: 14[ENC] generating ID_PROT request 0 [ ID HASH ]
Mar 02 10:40:22 xps charon[6221]: 14[NET] sending packet: from 10.0.1.58[4500] to 71.89.153.210[4500] (68 bytes)
Mar 02 10:40:22 xps charon[6221]: 15[NET] received packet: from 71.89.153.210[4500] to 10.0.1.58[4500] (76 bytes)
Mar 02 10:40:22 xps charon[6221]: 15[IKE] queueing TRANSACTION request as tasks still active
Mar 02 10:40:26 xps charon[6221]: 05[IKE] sending retransmit 1 of request message ID 0, seq 3
Mar 02 10:40:26 xps charon[6221]: 05[NET] sending packet: from 10.0.1.58[4500] to 71.89.153.210[4500] (68 bytes)
Mar 02 10:40:26 xps charon[6221]: 06[NET] received packet: from 71.89.153.210[4500] to 10.0.1.58[4500] (92 bytes)
Mar 02 10:40:26 xps charon[6221]: 06[ENC] parsed ID_PROT response 0 [ ID HASH N(INITIAL_CONTACT) ]
Mar 02 10:40:26 xps charon[6221]: 06[IKE] IKE_SA e30e20a1-6f99-46d8-9e7e-2007356cff21[1] established between 10.0.1.58[10.0.1.58]...71.89.153.210[71.89.153.210]
Mar 02 10:40:26 xps charon[6221]: 06[IKE] IKE_SA e30e20a1-6f99-46d8-9e7e-2007356cff21[1] established between 10.0.1.58[10.0.1.58]...71.89.153.210[71.89.153.210]
Mar 02 10:40:26 xps charon[6221]: 06[IKE] scheduling reauthentication in 10139s
Mar 02 10:40:26 xps charon[6221]: 06[IKE] maximum IKE_SA lifetime 10679s
Mar 02 10:40:26 xps charon[6221]: 06[ENC] parsed TRANSACTION request 3938256919 [ HASH CPRQ(X_TYPE X_USER X_PWD) ]
Mar 02 10:40:26 xps charon[6221]: 06[ENC] generating TRANSACTION response 3938256919 [ HASH CP ]
Mar 02 10:40:26 xps charon[6221]: 06[NET] sending packet: from 10.0.1.58[4500] to 71.89.153.210[4500] (68 bytes)
Mar 02 10:40:26 xps charon[6221]: 06[ENC] generating QUICK_MODE request 1430309094 [ HASH SA No ID ID NAT-OA NAT-OA ]
Mar 02 10:40:26 xps charon[6221]: 06[NET] sending packet: from 10.0.1.58[4500] to 71.89.153.210[4500] (244 bytes)
Mar 02 10:40:26 xps charon[6221]: 08[NET] received packet: from 71.89.153.210[4500] to 10.0.1.58[4500] (172 bytes)
Mar 02 10:40:26 xps charon[6221]: 08[ENC] parsed QUICK_MODE response 1430309094 [ HASH SA No ID ID NAT-OA NAT-OA ]
Mar 02 10:40:26 xps charon[6221]: 08[CFG] selected proposal: ESP:3DES_CBC/HMAC_SHA1_96/NO_EXT_SEQ
Mar 02 10:40:26 xps charon[6221]: 08[IKE] CHILD_SA e30e20a1-6f99-46d8-9e7e-2007356cff21{1} established with SPIs c8170e4f_i 8a306b8f_o and TS 10.0.1.58/32[udp/l2f] === 71.89.153.210/32[udp/l2f]
Mar 02 10:40:26 xps charon[6221]: 08[IKE] CHILD_SA e30e20a1-6f99-46d8-9e7e-2007356cff21{1} established with SPIs c8170e4f_i 8a306b8f_o and TS 10.0.1.58/32[udp/l2f] === 71.89.153.210/32[udp/l2f]
Mar 02 10:40:26 xps charon[6221]: 08[ENC] generating QUICK_MODE request 1430309094 [ HASH ]
Mar 02 10:40:26 xps NetworkManager[6250]: initiating Main Mode IKE_SA e30e20a1-6f99-46d8-9e7e-2007356cff21[1] to 71.89.153.210
Mar 02 10:40:26 xps NetworkManager[6250]: generating ID_PROT request 0 [ SA V V V V V ]
Mar 02 10:40:26 xps NetworkManager[6250]: sending packet: from 10.0.1.58[500] to 71.89.153.210[500] (532 bytes)
Mar 02 10:40:26 xps NetworkManager[6250]: received packet: from 71.89.153.210[500] to 10.0.1.58[500] (112 bytes)
Mar 02 10:40:26 xps NetworkManager[6250]: parsed ID_PROT response 0 [ SA V V ]
Mar 02 10:40:26 xps NetworkManager[6250]: received unknown vendor ID: 5b:36:2b:c8:20:f6:00:07
Mar 02 10:40:26 xps NetworkManager[6250]: received NAT-T (RFC 3947) vendor ID
Mar 02 10:40:26 xps NetworkManager[6250]: selected proposal: IKE:3DES_CBC/HMAC_SHA1_96/PRF_HMAC_SHA1/MODP_1024
Mar 02 10:40:26 xps NetworkManager[6250]: generating ID_PROT request 0 [ KE No NAT-D NAT-D ]
Mar 02 10:40:26 xps NetworkManager[6250]: sending packet: from 10.0.1.58[500] to 71.89.153.210[500] (244 bytes)
Mar 02 10:40:26 xps NetworkManager[6250]: received packet: from 71.89.153.210[500] to 10.0.1.58[500] (276 bytes)
Mar 02 10:40:26 xps NetworkManager[6250]: parsed ID_PROT response 0 [ KE NAT-D NAT-D No V V V ]
Mar 02 10:40:26 xps NetworkManager[6250]: received unknown vendor ID: 40:4b:f4:39:52:2c:a3:f6
Mar 02 10:40:26 xps NetworkManager[6250]: received XAuth vendor ID
Mar 02 10:40:26 xps NetworkManager[6250]: received DPD vendor ID
Mar 02 10:40:26 xps NetworkManager[6250]: local host is behind NAT, sending keep alives
Mar 02 10:40:26 xps NetworkManager[6250]: generating ID_PROT request 0 [ ID HASH ]
Mar 02 10:40:26 xps NetworkManager[6250]: sending packet: from 10.0.1.58[4500] to 71.89.153.210[4500] (68 bytes)
Mar 02 10:40:26 xps NetworkManager[6250]: received packet: from 71.89.153.210[4500] to 10.0.1.58[4500] (76 bytes)
Mar 02 10:40:26 xps NetworkManager[6250]: queueing TRANSACTION request as tasks still active
Mar 02 10:40:26 xps NetworkManager[6250]: sending retransmit 1 of request message ID 0, seq 3
Mar 02 10:40:26 xps NetworkManager[6250]: sending packet: from 10.0.1.58[4500] to 71.89.153.210[4500] (68 bytes)
Mar 02 10:40:26 xps NetworkManager[6250]: received packet: from 71.89.153.210[4500] to 10.0.1.58[4500] (92 bytes)
Mar 02 10:40:26 xps NetworkManager[6250]: parsed ID_PROT response 0 [ ID HASH N(INITIAL_CONTACT) ]
Mar 02 10:40:26 xps NetworkManager[6250]: IKE_SA e30e20a1-6f99-46d8-9e7e-2007356cff21[1] established between 10.0.1.58[10.0.1.58]...71.89.153.210[71.89.153.210]
Mar 02 10:40:26 xps NetworkManager[6250]: scheduling reauthentication in 10139s
Mar 02 10:40:26 xps NetworkManager[6250]: maximum IKE_SA lifetime 10679s
Mar 02 10:40:26 xps NetworkManager[6250]: parsed TRANSACTION request 3938256919 [ HASH CPRQ(X_TYPE X_USER X_PWD) ]
Mar 02 10:40:26 xps NetworkManager[6250]: generating TRANSACTION response 3938256919 [ HASH CP ]
Mar 02 10:40:26 xps NetworkManager[6250]: sending packet: from 10.0.1.58[4500] to 71.89.153.210[4500] (68 bytes)
Mar 02 10:40:26 xps NetworkManager[6250]: generating QUICK_MODE request 1430309094 [ HASH SA No ID ID NAT-OA NAT-OA ]
Mar 02 10:40:26 xps NetworkManager[6250]: sending packet: from 10.0.1.58[4500] to 71.89.153.210[4500] (244 bytes)
Mar 02 10:40:26 xps NetworkManager[6250]: received packet: from 71.89.153.210[4500] to 10.0.1.58[4500] (172 bytes)
Mar 02 10:40:26 xps NetworkManager[6250]: parsed QUICK_MODE response 1430309094 [ HASH SA No ID ID NAT-OA NAT-OA ]
Mar 02 10:40:26 xps charon[6221]: 08[NET] sending packet: from 10.0.1.58[4500] to 71.89.153.210[4500] (60 bytes)
Mar 02 10:40:26 xps NetworkManager[6250]: selected proposal: ESP:3DES_CBC/HMAC_SHA1_96/NO_EXT_SEQ
Mar 02 10:40:26 xps NetworkManager[6250]: CHILD_SA e30e20a1-6f99-46d8-9e7e-2007356cff21{1} established with SPIs c8170e4f_i 8a306b8f_o and TS 10.0.1.58/32[udp/l2f] === 71.89.153.210/32[udp/l2f]
Mar 02 10:40:26 xps NetworkManager[6250]: generating QUICK_MODE request 1430309094 [ HASH ]
Mar 02 10:40:26 xps NetworkManager[6250]: connection 'e30e20a1-6f99-46d8-9e7e-2007356cff21' established successfully
Mar 02 10:40:26 xps charon[6221]: 07[NET] received packet: from 71.89.153.210[4500] to 10.0.1.58[4500] (84 bytes)
Mar 02 10:40:26 xps charon[6221]: 07[ENC] parsed INFORMATIONAL_V1 request 4257504994 [ HASH D ]
Mar 02 10:40:26 xps charon[6221]: 07[IKE] received DELETE for IKE_SA e30e20a1-6f99-46d8-9e7e-2007356cff21[1]
Mar 02 10:40:26 xps charon[6221]: 07[IKE] deleting IKE_SA e30e20a1-6f99-46d8-9e7e-2007356cff21[1] between 10.0.1.58[10.0.1.58]...71.89.153.210[71.89.153.210]
Mar 02 10:40:26 xps charon[6221]: 07[IKE] deleting IKE_SA e30e20a1-6f99-46d8-9e7e-2007356cff21[1] between 10.0.1.58[10.0.1.58]...71.89.153.210[71.89.153.210]
Mar 02 10:40:26 xps NetworkManager[6296]: Stopping strongSwan IPsec...
Mar 02 10:40:26 xps charon[6221]: 00[DMN] signal of type SIGINT received. Shutting down
Mar 02 10:40:26 xps ipsec_starter[6220]: child 6221 (charon) has quit (exit code 0)
Mar 02 10:40:26 xps ipsec_starter[6220]: 
Mar 02 10:40:26 xps ipsec_starter[6220]: charon stopped after 200 ms
Mar 02 10:40:26 xps ipsec_starter[6220]: ipsec starter stopped
Mar 02 10:40:26 xps nm-l2tp-service[6195]: g_dbus_method_invocation_take_error: assertion 'error != NULL' failed
Mar 02 10:40:26 xps NetworkManager[6090]: <info>  [1614699626.7743] vpn-connection[0x558f0fafe0f0,e30e20a1-6f99-46d8-9e7e-2007356cff21,"Company",0]: VPN plugin: state changed: stopped (6)
Mar 02 10:40:26 xps NetworkManager[6090]: <info>  [1614699626.7816] vpn-connection[0x558f0fafe0f0,e30e20a1-6f99-46d8-9e7e-2007356cff21,"Company",0]: VPN service disappeared
Mar 02 10:40:26 xps NetworkManager[6090]: <warn>  [1614699626.7855] vpn-connection[0x558f0fafe0f0,e30e20a1-6f99-46d8-9e7e-2007356cff21,"Company",0]: VPN connection: failed to connect: 'Message recipient disconnected from message bus without replying'
```

This is all while using the following settings for the VPN connection:
```
Enable IPsec tunnel to L2TP host
Using a PSK
Using MSCHAPv2 for auth
```

Using:
```
Ubuntu 20.04.2
Network Manager v1.22.10
xl2tp v1.3.12
ipsec/strongswan U5.8.2/K5.8.0-44-generic
```

I've also tried using ike-scan to see what phase1/phase2 algorithms the server uses, but setting them manually to the correct values ('3des-sha1-modp1024' for phase 1, '3des-sha1' for phase 2) doesn't seem to make a difference.

Any help figuring this out would be greatly appreciated!

---

