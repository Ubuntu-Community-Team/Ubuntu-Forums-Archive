---
title: "Working Strongswan just blew up"
date: 2015-03-01
forum: Networking &amp; Wireless
---

### Post by DigiAngel on 2015-03-01
And I don't even know what to look at...config is super simple.  External IP on one interface, internal on the other (192.168.1.1) box acts as a router.


```
Mar  1 17:21:52 gateway charon: 01[NET] sending packet: from server.ext.ip[4500] to client.ext.ip[61562] (2204 bytes)
Mar  1 17:22:15 gateway charon: 12[NET] received packet: from client.ext.ip[61562] to server.ext.ip[4500] (1916 bytes)
Mar  1 17:22:15 gateway charon: 12[ENC] parsed IKE_AUTH request 1 [ IDi CERT N(INIT_CONTACT) CERTREQ IDr AUTH CPRQ(ADDR DNS) SA TSi TSr N(MOBIKE_SUP) N(ADD_4_ADDR) N(MULT_AUTH) N(EAP_ONLY) ]
Mar  1 17:22:15 gateway charon: 12[IKE] received retransmit of request with ID 1, retransmitting response

```

Server ipsec.conf:
```
conn rw	
	leftsubnet=192.168.1.0/24
	leftcert=StrongSwanHostCert.pem
	right=%any
	rightsourceip=192.168.1.11
	auto=add

```

No clue why this is suddenly not working...it was working fine a few weeks ago.  Please help...thank you.

---

### Post by DigiAngel on 2015-03-02
Well this was new....after taking the laptop and putting it on a remote network, it ran like a champ as expected...connection, no retransmissions, no issues at all...packets flowed and I could ping what I needed.  So....what changed?  The OS on the phone I was using for tethering. Let the records show that not all tethering is equal I guess.

---

