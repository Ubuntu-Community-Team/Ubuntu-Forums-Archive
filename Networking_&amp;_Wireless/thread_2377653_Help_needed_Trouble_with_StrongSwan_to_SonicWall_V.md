---
title: "Help needed: Trouble with StrongSwan to SonicWall VPN using IKEv1/XAUTH"
date: 2017-11-15
forum: Networking &amp; Wireless
---

### Post by jbhtexas on 2017-11-15
Hello !

I have upgraded from Ubuntu 14.04 LTS to 16.04 LTS and am having trouble getting a VPN connection established to a SonicWall firewall using IKEv1 and XAUTH.  Ubuntu 14.04 used OpenSwan, and I had a working setup there.  Ubuntu 16.04 uses StrongSwan 5.3.5 by default, which is known to have a bug with SonicWall firewalls (see [https://wiki.strongswan.org/issues/1434](https://wiki.strongswan.org/issues/1434)).  The bug supposedly was fixed in 5.5.0, so I have built StrongSwan 5.6.0 locally.

The firewall is configured to use IKEv1 with PSK and XAUTH.  What happened in Ubuntu 14.04/OpenSwan was that I would start the connection with "ipsec up myconn", there would be a prompt to enter username and password (the username/password database is on the SonicWall), and the connection would finish.  What happens with StrongSwan is that it appears that Phase 1 finishes, but there is no prompt for username and password, and then the connection fails.  From the logs, it seems that both sides are waiting for the other to do something after Phase 1 completes.

Most likely, the problem has to do with something set wrong in the configuration file.  I migrated my old ipsec.conf file, and there are some significant differences between parameters supported in the OpenSwan and StrongSwan ipsec.conf files, so I probably have messed something up...perhaps with leftauth/leftauth2, rightauth/rightauth2.  I have tried various combinations of these,and also tried xauth_eap, but that doesn't change anything.  In the ipsec output, it seems that the client is looking for a username/password in a file instead of prompting for one.  In reading through the StrongSwan docs, it seems that StrongSwan can prompt for a username and password, buy maybe I have misread that.

SonicWall Log
```
1	11/15/2017 10:34:02.176	Info	VPN IKE	IKE Responder: Remote party timeout - Retransmitting IKE request.	98.xxx.xxx.xxx, 4500	192.yyy.yyy.yyy, 4500	VPN Policy: WAN GroupVPN	 
2	11/15/2017 10:33:51.176	Info	VPN IKE	IKE Responder: Remote party timeout - Retransmitting IKE request.	98.xxx.xxx.xxx, 4500	192.yyy.yyy.yyy, 4500	VPN Policy: WAN GroupVPN	 
3	11/15/2017 10:33:44.592	Info	VPN IKE	IKE Responder: Received Aggressive Mode request (Phase 1)	192.yyy.yyy.yyy 4500 (admin)	98.xxx.xxx.xxx, 4500		 
5	11/15/2017 10:33:14.592	Info	VPN IKE	IKE Responder: Aggressive Mode complete (Phase 1)	192.yyy.yyy.yyy, 4500 (admin)	98.xxx.xxx.xxx, 4500	VPN Policy: WAN GroupVPN;3DES; MD5; DH Group 2; lifetime=10800 secs	 
6	11/15/2017 10:33:14.592	Info	VPN IKE	NAT Discovery : Peer IPSec Security Gateway behind a NAT/NAPT Device		 		 
7	11/15/2017 10:33:14.592	Info	VPN IKE	NAT Discovery : Local IPSec Security Gateway behind a NAT/NAPT Device		 		 
8	11/15/2017 10:33:14.544	Info	VPN IKE	IKE Responder: Received Aggressive Mode request (Phase 1)	192.yyy.yyy.yyy, 500 (admin)	98.xxx.xxx.xxx, 500	
```

IPSEC output
```
initiating Aggressive Mode IKE_SA APC[1] to 98.xxx.xxx.xxx
generating AGGRESSIVE request 0 [ SA KE No ID V V V V V ]
sending packet: from 192.yyy.yyy.yyy[500] to 98.xxx.xxx.xxx[500] (360 bytes)
received packet: from 98.xxx.xxx.xxx[500] to 192.yyy.yyy.yyy[500] (386 bytes)
parsed AGGRESSIVE response 0 [ SA KE No ID V V V NAT-D NAT-D V V HASH ]
received unknown vendor ID: 40:4b:f4:39:52:2c:a3:f6
received unknown vendor ID: 5b:36:2b:c8:20:f6:00:07
received NAT-T (RFC 3947) vendor ID
received DPD vendor ID
received XAuth vendor ID
local host is behind NAT, sending keep alives
generating AGGRESSIVE request 0 [ HASH NAT-D NAT-D ]
sending packet: from 192.yyy.yyy.yyy[4500] to 98.xxx.xxx.xxx[4500] (92 bytes)
received packet: from 98.xxx.xxx.xxx[4500] to 192.yyy.yyy.yyy[4500] (76 bytes)
parsed TRANSACTION request 3963242572 [ HASH CPRQ(X_TYPE X_USER X_PWD) ]
no XAuth password found for 'GroupVPN' - 'APCNet'
generating TRANSACTION response 3963242572 [ HASH CP ]
sending packet: from 192.yyy.yyy.yyy[4500] to 98.xxx.xxx.xxx[4500] (60 bytes)
received packet: from 98.xxx.xxx.xxx[4500] to 192.yyy.yyy.yyy[4500] (84 bytes)
queueing INFORMATIONAL_V1 request as tasks still active
received packet: from 98.xxx.xxx.xxx[4500] to 192.yyy.yyy.yyy[4500] (84 bytes)
ignoring INFORMATIONAL_V1 request, queue full
sending keep alive to 98.xxx.xxx.xxx[4500]
peer did not initiate expected exchange, reestablishing IKE_SA
reinitiating IKE_SA APC[1]
initiating Aggressive Mode IKE_SA APC[1] to 98.xxx.xxx.xxx
generating AGGRESSIVE request 0 [ SA KE No ID V V V V V ]
sending packet: from 192.yyy.yyy.yyy[4500] to 98.xxx.xxx.xxx[4500] (360 bytes)
establishing connection 'APC' failed
No leaks detected, 2 suppressed by whitelist

```

ipsec.conf
```
conn APC
	type=tunnel
	left=%defaultroute
	leftid=@GroupVPN
	leftauth=psk
	leftauth2=xauth
	right=98.xxx.xxx.xxx
     	rightsubnet=10.0.15.0/24
	rightid=@APCNet
	rightauth=psk
	rightauth2=xauth
	xauth=client
	keyexchange=ikev1
	keyingtries=3
	aggressive=yes
	auto=add
	ike=3des-md5-modp1024!
	esp=3des-md5-modp1024!
```

Any help would be greatly appreciated!
Thanks!

---

