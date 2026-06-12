---
title: "L2tp VPN"
date: 2018-11-28
forum: Networking &amp; Wireless
---

### Post by Cider on 2018-11-28
Hello, 

Been struggling setting up a L2TP vpn from my ubuntu laptop to my home network. I am using a Safe@Office 1000N at home. 

Here is the output of syslog 

```
@<pcname>-lp:/etc$ tail -f /var/log/syslog
Nov 28 09:45:49 <pcname>-lp kernel: [ 4025.950575] audit: type=1400 audit(1543391149.611:109): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/usr/lib/ipsec/charon" pid=8256 comm="apparmor_parser"
Nov 28 09:45:49 <pcname>-lp dbus-daemon[746]: Unknown group "power" in message bus configuration file
Nov 28 09:45:49 <pcname>-lp dbus-daemon[746]: [system] Reloaded configuration
Nov 28 09:46:36 <pcname>-lp gnome-software[1764]: failed to rescan: No valid root node specified
Nov 28 09:46:41 <pcname>-lp gnome-software[1764]: Only 0 apps for recent list, hiding
Nov 28 09:46:42 <pcname>-lp gnome-software[1764]: tried overwriting gitkraken key GnomeSoftware::FeatureTile-css from border-color: #000000;#012text-shadow: 0 1px 1px rgba(255,255,255,0.5);#012color: #000000;#012outline-offset: 0;#012outline-color: alpha(#ffffff, 0.75);#012outline-style: dashed;#012outline-offset: 2px;#012background: url('/home/tyron/.cache/gnome-software/cssresource/5ba0e9b2cc79a8afd469b183a4006929bcc39b00-banner-icon_vWkDBG3.png') left center / auto 100% no-repeat, url('/home/tyron/.cache/gnome-software/cssresource/7ed6277a9d365314e110e32a746f14aaaee41506-banner_wDoKy9V.png') center / cover no-repeat;; to border-color: #000000;#012text-shadow: 0 1px 1px rgba(255,255,255,0.5);#012color: #000000;#012outline-offset: 0;#012outline-color: alpha(#ffffff, 0.75);#012outline-style: dashed;#012outline-offset: 2px;#012background: url('https://dashboard.snapcraft.io/site_media/appmedia/2018/11/banner-icon_vWkDBG3.png') left center / auto 100% no-repeat, url('https://dashboard.snapcraft.io/site_media/appmedia/2018/11/banner_wDoKy9V.png') center / cover no-repeat;;
Nov 28 09:48:25 <pcname>-lp gnome-control-c[2193]: ((libnm-core/nm-setting-vpn.c:193)): assertion '<dropped>' failed
Nov 28 09:48:36 <pcname>-lp gnome-control-c[2193]: message repeated 3 times: [ ((libnm-core/nm-setting-vpn.c:193)): assertion '<dropped>' failed]
Nov 28 09:48:41 <pcname>-lp NetworkManager[756]: <info>  [1543391321.7656] keyfile: add connection /etc/NetworkManager/system-connections/home (1238083b-5050-4e92-837f-e147b3056963,"home")
Nov 28 09:48:41 <pcname>-lp NetworkManager[756]: <info>  [1543391321.7665] audit: op="connection-add" uuid="1238083b-5050-4e92-837f-e147b3056963" name="home" pid=2193 uid=1000 result="success"
Nov 28 09:49:01 <pcname>-lp NetworkManager[756]: <info>  [1543391341.1685] audit: op="connection-activate" uuid="1238083b-5050-4e92-837f-e147b3056963" name="home" pid=1454 uid=1000 result="success"
Nov 28 09:49:01 <pcname>-lp gnome-shell[921]: JS ERROR: TypeError: item is undefined#012setActiveConnections/<@resource:///org/gnome/shell/ui/status/network.js:1518:17#012setActiveConnections@resource:///org/gnome/shell/ui/status/network.js:1515:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_syncVpnConnections@resource:///org/gnome/shell/ui/status/network.js:1853:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22
Nov 28 09:49:01 <pcname>-lp NetworkManager[756]: <info>  [1543391341.1853] vpn-connection[0x55ecb82ee710,1238083b-5050-4e92-837f-e147b3056963,"home",0]: Started the VPN service, PID 8393
Nov 28 09:49:01 <pcname>-lp NetworkManager[756]: <info>  [1543391341.1965] vpn-connection[0x55ecb82ee710,1238083b-5050-4e92-837f-e147b3056963,"home",0]: Saw the service appear; activating connection
Nov 28 09:49:01 <pcname>-lp NetworkManager[756]: <info>  [1543391341.2890] vpn-connection[0x55ecb82ee710,1238083b-5050-4e92-837f-e147b3056963,"home",0]: VPN connection: (ConnectInteractive) reply received
Nov 28 09:49:01 <pcname>-lp nm-l2tp-service[8393]: Check port 1701
Nov 28 09:49:01 <pcname>-lp NetworkManager[756]: Stopping strongSwan IPsec...
Nov 28 09:49:01 <pcname>-lp charon: 00[DMN] signal of type SIGINT received. Shutting down
Nov 28 09:49:01 <pcname>-lp ipsec[8217]: 00[DMN] Starting IKE charon daemon (strongSwan 5.6.2, Linux 4.15.0-39-generic, x86_64)
Nov 28 09:49:01 <pcname>-lp ipsec[8217]: 00[CFG] loading ca certificates from '/etc/ipsec.d/cacerts'
Nov 28 09:49:01 <pcname>-lp ipsec[8217]: 00[CFG] loading aa certificates from '/etc/ipsec.d/aacerts'
Nov 28 09:49:01 <pcname>-lp ipsec[8217]: 00[CFG] loading ocsp signer certificates from '/etc/ipsec.d/ocspcerts'
Nov 28 09:49:01 <pcname>-lp ipsec[8217]: 00[CFG] loading attribute certificates from '/etc/ipsec.d/acerts'
Nov 28 09:49:01 <pcname>-lp ipsec[8217]: 00[CFG] loading crls from '/etc/ipsec.d/crls'
Nov 28 09:49:01 <pcname>-lp ipsec[8217]: 00[CFG] loading secrets from '/etc/ipsec.secrets'
Nov 28 09:49:01 <pcname>-lp ipsec[8217]: 00[CFG] loading secrets from '/etc/ipsec.d/nm-l2tp-ipsec-7a54769f-22c5-4874-bffe-b07d6a137ce9.secrets'
Nov 28 09:49:01 <pcname>-lp ipsec[8217]: 00[CFG]   loaded IKE secret for %any
Nov 28 09:49:01 <pcname>-lp ipsec[8217]: 00[LIB] loaded plugins: charon aesni aes rc2 sha2 sha1 md4 md5 mgf1 random nonce x509 revocation constraints pubkey pkcs1 pkcs7 pkcs8 pkcs12 pgp dnskey sshkey pem openssl fips-prf gmp agent xcbc hmac gcm attr kernel-netlink resolve socket-default connmark stroke updown eap-mschapv2 xauth-generic counters
Nov 28 09:49:01 <pcname>-lp ipsec[8217]: 00[LIB] dropped capabilities, running as uid 0, gid 0
Nov 28 09:49:01 <pcname>-lp ipsec[8217]: 00[JOB] spawning 16 worker threads
Nov 28 09:49:01 <pcname>-lp ipsec[8217]: 00[DMN] signal of type SIGINT received. Shutting down
Nov 28 09:49:01 <pcname>-lp ipsec[8217]: charon stopped after 200 ms
Nov 28 09:49:01 <pcname>-lp ipsec[8217]: ipsec starter stopped
Nov 28 09:49:03 <pcname>-lp NetworkManager[756]: Starting strongSwan 5.6.2 IPsec [starter]...
Nov 28 09:49:03 <pcname>-lp NetworkManager[756]: Loading config setup
Nov 28 09:49:03 <pcname>-lp NetworkManager[756]: Loading conn '1238083b-5050-4e92-837f-e147b3056963'
Nov 28 09:49:03 <pcname>-lp NetworkManager[756]: found netkey IPsec stack
Nov 28 09:49:03 <pcname>-lp charon: 00[DMN] Starting IKE charon daemon (strongSwan 5.6.2, Linux 4.15.0-39-generic, x86_64)
Nov 28 09:49:03 <pcname>-lp charon: 00[CFG] loading ca certificates from '/etc/ipsec.d/cacerts'
Nov 28 09:49:03 <pcname>-lp charon: 00[CFG] loading aa certificates from '/etc/ipsec.d/aacerts'
Nov 28 09:49:03 <pcname>-lp charon: 00[CFG] loading ocsp signer certificates from '/etc/ipsec.d/ocspcerts'
Nov 28 09:49:03 <pcname>-lp charon: 00[CFG] loading attribute certificates from '/etc/ipsec.d/acerts'
Nov 28 09:49:03 <pcname>-lp charon: 00[CFG] loading crls from '/etc/ipsec.d/crls'
Nov 28 09:49:03 <pcname>-lp charon: 00[CFG] loading secrets from '/etc/ipsec.secrets'
Nov 28 09:49:03 <pcname>-lp charon: 00[CFG] loading secrets from '/etc/ipsec.d/nm-l2tp-ipsec-1238083b-5050-4e92-837f-e147b3056963.secrets'
Nov 28 09:49:03 <pcname>-lp charon: 00[CFG]   loaded IKE secret for %any
Nov 28 09:49:03 <pcname>-lp charon: 00[CFG] loading secrets from '/etc/ipsec.d/nm-l2tp-ipsec-7a54769f-22c5-4874-bffe-b07d6a137ce9.secrets'
Nov 28 09:49:03 <pcname>-lp charon: 00[CFG]   loaded IKE secret for %any
Nov 28 09:49:03 <pcname>-lp charon: 00[LIB] loaded plugins: charon aesni aes rc2 sha2 sha1 md4 md5 mgf1 random nonce x509 revocation constraints pubkey pkcs1 pkcs7 pkcs8 pkcs12 pgp dnskey sshkey pem openssl fips-prf gmp agent xcbc hmac gcm attr kernel-netlink resolve socket-default connmark stroke updown eap-mschapv2 xauth-generic counters
Nov 28 09:49:03 <pcname>-lp charon: 00[LIB] dropped capabilities, running as uid 0, gid 0
Nov 28 09:49:03 <pcname>-lp charon: 00[JOB] spawning 16 worker threads
Nov 28 09:49:03 <pcname>-lp charon: 05[CFG] received stroke: add connection '1238083b-5050-4e92-837f-e147b3056963'
Nov 28 09:49:03 <pcname>-lp charon: 05[CFG] added configuration '1238083b-5050-4e92-837f-e147b3056963'
Nov 28 09:49:04 <pcname>-lp charon: 06[CFG] rereading secrets
Nov 28 09:49:04 <pcname>-lp charon: 06[CFG] loading secrets from '/etc/ipsec.secrets'
Nov 28 09:49:04 <pcname>-lp charon: 06[CFG] loading secrets from '/etc/ipsec.d/nm-l2tp-ipsec-1238083b-5050-4e92-837f-e147b3056963.secrets'
Nov 28 09:49:04 <pcname>-lp charon: 06[CFG]   loaded IKE secret for %any
Nov 28 09:49:04 <pcname>-lp charon: 06[CFG] loading secrets from '/etc/ipsec.d/nm-l2tp-ipsec-7a54769f-22c5-4874-bffe-b07d6a137ce9.secrets'
Nov 28 09:49:04 <pcname>-lp charon: 06[CFG]   loaded IKE secret for %any
Nov 28 09:49:04 <pcname>-lp charon: 09[CFG] received stroke: initiate '1238083b-5050-4e92-837f-e147b3056963'
Nov 28 09:49:04 <pcname>-lp charon: 11[IKE] initiating Main Mode IKE_SA 1238083b-5050-4e92-837f-e147b3056963[1] to X.X.X.X
Nov 28 09:49:04 <pcname>-lp charon: 11[ENC] generating ID_PROT request 0 [ SA V V V V V ]
Nov 28 09:49:04 <pcname>-lp charon: 11[NET] sending packet: from X.X.14.20[500] to X.X.X.X[500] (236 bytes)
Nov 28 09:49:04 <pcname>-lp charon: 08[NET] received packet: from X.X.X.X[500] to X.X.14.20[500] (100 bytes)
Nov 28 09:49:04 <pcname>-lp charon: 08[ENC] parsed ID_PROT response 0 [ SA V ]
Nov 28 09:49:04 <pcname>-lp charon: 08[IKE] received draft-ietf-ipsec-nat-t-ike-02\n vendor ID
Nov 28 09:49:04 <pcname>-lp charon: 08[ENC] generating ID_PROT request 0 [ KE No NAT-D NAT-D ]
Nov 28 09:49:04 <pcname>-lp charon: 08[NET] sending packet: from X.X.14.20[500] to X.X.X.X[500] (244 bytes)
Nov 28 09:49:04 <pcname>-lp charon: 13[NET] received packet: from X.X.X.X[500] to X.X.14.20[500] (232 bytes)
Nov 28 09:49:04 <pcname>-lp charon: 13[ENC] parsed ID_PROT response 0 [ KE No NAT-D NAT-D ]
Nov 28 09:49:04 <pcname>-lp charon: 13[IKE] local host is behind NAT, sending keep alives
Nov 28 09:49:04 <pcname>-lp charon: 13[ENC] generating ID_PROT request 0 [ ID HASH ]
Nov 28 09:49:04 <pcname>-lp charon: 13[NET] sending packet: from X.X.14.20[4500] to X.X.X.X[4500] (68 bytes)
Nov 28 09:49:05 <pcname>-lp charon: 14[NET] received packet: from X.X.X.X[4500] to X.X.14.20[4500] (68 bytes)
Nov 28 09:49:05 <pcname>-lp charon: 14[ENC] parsed ID_PROT response 0 [ ID HASH ]
Nov 28 09:49:05 <pcname>-lp charon: 14[IKE] IKE_SA 1238083b-5050-4e92-837f-e147b3056963[1] established between X.X.14.20[X.X.14.20]...X.X.X.X[X.X.X.X]
Nov 28 09:49:05 <pcname>-lp charon: 14[IKE] scheduling reauthentication in 10039s
Nov 28 09:49:05 <pcname>-lp charon: 14[IKE] maximum IKE_SA lifetime 10579s
Nov 28 09:49:05 <pcname>-lp charon: 14[ENC] generating QUICK_MODE request 2500550118 [ HASH SA No ID ID NAT-OA NAT-OA ]
Nov 28 09:49:05 <pcname>-lp charon: 14[NET] sending packet: from X.X.14.20[4500] to X.X.X.X[4500] (220 bytes)
Nov 28 09:49:05 <pcname>-lp charon: 15[NET] received packet: from X.X.X.X[4500] to X.X.14.20[4500] (156 bytes)
Nov 28 09:49:05 <pcname>-lp charon: 15[ENC] parsed QUICK_MODE response 2500550118 [ HASH SA No ID ID ]
Nov 28 09:49:05 <pcname>-lp charon: 15[IKE] CHILD_SA 1238083b-5050-4e92-837f-e147b3056963{1} established with SPIs c657c26c_i ef202e6c_o and TS X.X.14.20/32[udp/l2f] === X.X.X.X/32[udp/l2f]
Nov 28 09:49:05 <pcname>-lp charon: 15[ENC] generating QUICK_MODE request 2500550118 [ HASH ]
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: initiating Main Mode IKE_SA 1238083b-5050-4e92-837f-e147b3056963[1] to X.X.X.X
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: generating ID_PROT request 0 [ SA V V V V V ]
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: sending packet: from X.X.14.20[500] to X.X.X.X[500] (236 bytes)
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: received packet: from X.X.X.X[500] to X.X.14.20[500] (100 bytes)
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: parsed ID_PROT response 0 [ SA V ]
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: received draft-ietf-ipsec-nat-t-ike-02\n vendor ID
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: generating ID_PROT request 0 [ KE No NAT-D NAT-D ]
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: sending packet: from X.X.14.20[500] to X.X.X.X[500] (244 bytes)
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: received packet: from X.X.X.X[500] to X.X.14.20[500] (232 bytes)
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: parsed ID_PROT response 0 [ KE No NAT-D NAT-D ]
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: local host is behind NAT, sending keep alives
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: generating ID_PROT request 0 [ ID HASH ]
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: sending packet: from X.X.14.20[4500] to X.X.X.X[4500] (68 bytes)
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: received packet: from X.X.X.X[4500] to X.X.14.20[4500] (68 bytes)
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: parsed ID_PROT response 0 [ ID HASH ]
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: IKE_SA 1238083b-5050-4e92-837f-e147b3056963[1] established between X.X.14.20[X.X.14.20]...X.X.X.X[X.X.X.X]
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: scheduling reauthentication in 10039s
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: maximum IKE_SA lifetime 10579s
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: generating QUICK_MODE request 2500550118 [ HASH SA No ID ID NAT-OA NAT-OA ]
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: sending packet: from X.X.14.20[4500] to X.X.X.X[4500] (220 bytes)
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: received packet: from X.X.X.X[4500] to X.X.14.20[4500] (156 bytes)
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: parsed QUICK_MODE response 2500550118 [ HASH SA No ID ID ]
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: CHILD_SA 1238083b-5050-4e92-837f-e147b3056963{1} established with SPIs c657c26c_i ef202e6c_o and TS X.X.14.20/32[udp/l2f] === X.X.X.X/32[udp/l2f]
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: connection '1238083b-5050-4e92-837f-e147b3056963' established successfully
Nov 28 09:49:05 <pcname>-lp charon: 15[NET] sending packet: from X.X.14.20[4500] to X.X.X.X[4500] (60 bytes)
Nov 28 09:49:05 <pcname>-lp nm-l2tp-service[8393]: xl2tpd started with pid 8483
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: Not looking for kernel SAref support.
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: Using l2tp kernel support.
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: xl2tpd version xl2tpd-1.3.10 started on <pcname>-lp PID:8483
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc.
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: Forked by Scott Balmos and David Stipp, (C) 2001
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: Inherited by Jeff McAdams, (C) 2002
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: Forked again by Xelerance ([www.xelerance.com](www.xelerance.com)) (C) 2006-2016
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: Listening on IP address 0.0.0.0, port 1701
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: Connecting to host X.X.X.X, port 1701
Nov 28 09:49:05 <pcname>-lp NetworkManager[756]: <info>  [1543391345.3863] vpn-connection[0x55ecb82ee710,1238083b-5050-4e92-837f-e147b3056963,"home",0]: VPN plugin: state changed: starting (3)
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: Connection established to X.X.X.X, 1701.  Local: 20282, Remote: 3465 (ref=0/0).
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: Calling on tunnel 20282
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: Call established with X.X.X.X, Local: 26281, Remote: 53968, Serial: 1 (ref=0/0)
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: start_pppd: I'm running:
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: "/usr/sbin/pppd"
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: "plugin"
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: "pppol2tp.so"
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: "pppol2tp"
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: "7"
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: "passive"
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: "nodetach"
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: ":"
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: "file"
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: "/var/run/nm-l2tp-ppp-options-1238083b-5050-4e92-837f-e147b3056963"
Nov 28 09:49:06 <pcname>-lp pppd[8484]: Plugin pppol2tp.so loaded.
Nov 28 09:49:06 <pcname>-lp pppd[8484]: Plugin /usr/lib/pppd/2.4.7/nm-l2tp-pppd-plugin.so loaded.
Nov 28 09:49:06 <pcname>-lp pppd[8484]: pppd 2.4.7 started by root, uid 0
Nov 28 09:49:06 <pcname>-lp pppd[8484]: Using interface ppp0
Nov 28 09:49:06 <pcname>-lp pppd[8484]: Connect: ppp0 <-->
Nov 28 09:49:06 <pcname>-lp pppd[8484]: Overriding mtu 1500 to 1400
Nov 28 09:49:06 <pcname>-lp pppd[8484]: Overriding mru 1500 to mtu value 1400
Nov 28 09:49:06 <pcname>-lp systemd-udevd[8487]: link_config: autonegotiation is unset or enabled, the speed and duplex are not writable.
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: <info>  [1543391346.4603] manager: (ppp0): new Ppp device (/org/freedesktop/NetworkManager/Devices/4)
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: <info>  [1543391346.4693] devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: <info>  [1543391346.4694] device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Nov 28 09:49:06 <pcname>-lp pppd[8484]: Overriding mtu 1500 to 1400
Nov 28 09:49:06 <pcname>-lp pppd[8484]: Overriding mru 1500 to mtu value 1400
Nov 28 09:49:06 <pcname>-lp pppd[8484]: EAP: peer reports authentication failure
Nov 28 09:49:06 <pcname>-lp pppd[8484]: Overriding mtu 1500 to 1400
Nov 28 09:49:06 <pcname>-lp pppd[8484]: Overriding mru 1500 to mtu value 1400
Nov 28 09:49:06 <pcname>-lp pppd[8484]: Connection terminated.
Nov 28 09:49:06 <pcname>-lp charon: 06[KNL] interface ppp0 deleted
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: death_handler: Fatal signal 15 received
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: Terminating pppd: sending TERM signal to pid 8484
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: xl2tpd[8483]: Connection 3465 closed to X.X.X.X, port 1701 (Server closing)
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: <warn>  [1543391346.5796] vpn-connection[0x55ecb82ee710,1238083b-5050-4e92-837f-e147b3056963,"home",0]: VPN plugin: failed: connect-failed (1)
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: Stopping strongSwan IPsec...
Nov 28 09:49:06 <pcname>-lp gnome-shell[921]: Removing a network device that was not added
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: <info>  [1543391346.5958] vpn-connection[0x55ecb82ee710,1238083b-5050-4e92-837f-e147b3056963,"home",0]: VPN plugin: state changed: stopping (5)
Nov 28 09:49:06 <pcname>-lp charon: 00[DMN] signal of type SIGINT received. Shutting down
Nov 28 09:49:06 <pcname>-lp gnome-shell[1454]: Removing a network device that was not added
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: <info>  [1543391346.5978] devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov 28 09:49:06 <pcname>-lp charon: 00[IKE] closing CHILD_SA 1238083b-5050-4e92-837f-e147b3056963{1} with SPIs c657c26c_i (389 bytes) ef202e6c_o (695 bytes) and TS X.X.14.20/32[udp/l2f] === X.X.X.X/32[udp/l2f]
Nov 28 09:49:06 <pcname>-lp charon: 00[IKE] sending DELETE for ESP CHILD_SA with SPI c657c26c
Nov 28 09:49:06 <pcname>-lp charon: 00[ENC] generating INFORMATIONAL_V1 request 1119188902 [ HASH D ]
Nov 28 09:49:06 <pcname>-lp charon: 00[NET] sending packet: from X.X.14.20[4500] to X.X.X.X[4500] (76 bytes)
Nov 28 09:49:06 <pcname>-lp charon: 00[IKE] deleting IKE_SA 1238083b-5050-4e92-837f-e147b3056963[1] between X.X.14.20[X.X.14.20]...X.X.X.X[X.X.X.X]
Nov 28 09:49:06 <pcname>-lp charon: 00[IKE] sending DELETE for IKE_SA 1238083b-5050-4e92-837f-e147b3056963[1]
Nov 28 09:49:06 <pcname>-lp charon: 00[ENC] generating INFORMATIONAL_V1 request 1128392469 [ HASH D ]
Nov 28 09:49:06 <pcname>-lp charon: 00[NET] sending packet: from X.X.14.20[4500] to X.X.X.X[4500] (84 bytes)
Nov 28 09:49:06 <pcname>-lp pppd[8484]: Exit.
Nov 28 09:49:06 <pcname>-lp nm-l2tp-service[8393]: ipsec shut down
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: <info>  [1543391346.7065] vpn-connection[0x55ecb82ee710,1238083b-5050-4e92-837f-e147b3056963,"home",0]: VPN plugin: state changed: stopped (6)
Nov 28 09:49:06 <pcname>-lp NetworkManager[756]: <info>  [1543391346.7114] vpn-connection[0x55ecb82ee710,1238083b-5050-4e92-837f-e147b3056963,"home",0]: VPN service disappeared
Nov 28 09:49:42 <pcname>-lp systemd-resolved[621]: Using degraded feature set (TCP) for DNS server fd58:197c:4d7a:0:16ae:dbff:fe55:c158.
Nov 28 09:49:42 <pcname>-lp systemd-resolved[621]: Using degraded feature set (UDP) for DNS server fd58:197c:4d7a:0:16ae:dbff:fe55:c158.
Nov 28 09:49:45 <pcname>-lp systemd-resolved[621]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Nov 28 09:49:45 <pcname>-lp systemd-resolved[621]: message repeated 15 times: [ Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.]
Nov 28 09:49:49 <pcname>-lp systemd-resolved[621]: Using degraded feature set (TCP) for DNS server fd58:197c:4d7a:0:16ae:dbff:fe55:c158.
Nov 28 09:49:51 <pcname>-lp systemd-resolved[621]: Using degraded feature set (UDP) for DNS server fd58:197c:4d7a:0:16ae:dbff:fe55:c158.
Nov 28 09:49:51 <pcname>-lp systemd-resolved[621]: Using degraded feature set (TCP) for DNS server fd58:197c:4d7a:0:16ae:dbff:fe55:c158.
Nov 28 09:49:51 <pcname>-lp systemd-resolved[621]: Using degraded feature set (UDP) for DNS server fd58:197c:4d7a:0:16ae:dbff:fe55:c158.
Nov 28 09:49:57 <pcname>-lp systemd-resolved[621]: Using degraded feature set (TCP) for DNS server fd58:197c:4d7a:0:16ae:dbff:fe55:c158.
Nov 28 09:49:57 <pcname>-lp systemd-resolved[621]: Using degraded feature set (UDP) for DNS server fd58:197c:4d7a:0:16ae:dbff:fe55:c158.
Nov 28 09:49:58 <pcname>-lp systemd-resolved[621]: Using degraded feature set (TCP) for DNS server fd58:197c:4d7a:0:16ae:dbff:fe55:c158.
Nov 28 09:50:02 <pcname>-lp systemd-resolved[621]: Using degraded feature set (UDP) for DNS server fd58:197c:4d7a:0:16ae:dbff:fe55:c158.
Nov 28 09:50:07 <pcname>-lp systemd-resolved[621]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Nov 28 09:50:07 <pcname>-lp systemd-resolved[621]: Server returned error NXDOMAIN, mitigating potential DNS violation DVE-2018-0001, retrying transaction with reduced feature level UDP.
Nov 28 09:50:10 <pcname>-lp systemd-resolved[621]: Using degraded feature set (TCP) for DNS server fd58:197c:4d7a:0:16ae:dbff:fe55:c158.
^C

```

On the VPN side I can see the following. 

```
Error: Failed to open L2TP tunnel with peer X.X.X.X User authentication failed: Could not locate user object: Timeout reached)
```

This works from a windows machine as well as my android phone. 

I used the following tutorial. 

[https://help.vpntunnel.com/support/solutions/articles/5000782608-vpntunnel-l2tp-installation-guide-for-ubuntu-18-04-](https://help.vpntunnel.com/support/solutions/articles/5000782608-vpntunnel-l2tp-installation-guide-for-ubuntu-18-04-)

any help is much appreciated.

---

