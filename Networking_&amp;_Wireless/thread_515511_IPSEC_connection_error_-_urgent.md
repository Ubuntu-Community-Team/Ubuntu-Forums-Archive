---
title: "IPSEC connection error - urgent"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by superbaby7 on 2007-08-02
Good afternoon

A user with Kubuntu 7.0.1 Linux  2.6.20-16-generic with packages  Racoon and quagga, connects via  ipsec tunnel to connect from his computer to remote (site) company. He can establish a connection and the remote company also uses Kubuntu 7.0.1 Linux  2.6.20-16-generic with packages Racoon and quagga (same setup)  can connect with this user by same ipsec tunnel. The problem occurs when the remote company sends traffic or information to the user through the IPSEC tunnel. The remote company confirms that they do not receive any reply from the user side y that information is not encrypted correctly  

I have pasted the contents of ipsec log below. How can the user solve this problem..??? 
Please help...!!:confused: 

IPSEC tunnel  log:

Jul 31 16:16:34 INT-MOVIL racoon: ERROR: such policy does not already exist: "195.55.47.11/32[0] 213.4.115.149/32[0] proto=any dir=in"
Jul 31 16:16:34 INT-MOVIL racoon: ERROR: such policy does not already exist: "213.4.115.149/32[0] 195.55.47.11/32[0] proto=any dir=out"
Jul 31 16:17:01 INT-MOVIL /USR/SBIN/CRON[2023]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 31 16:19:27 INT-MOVIL racoon: INFO: IPsec-SA expired: ESP/Transport 195.55.47.11[0]->213.4.115.149[0] spi=25716317(0x188665d)
Jul 31 16:19:28 INT-MOVIL racoon: INFO: IPsec-SA expired: ESP/Transport 213.4.115.149[0]->195.55.47.11[0] spi=3802560495(0xe2a677ef)
Jul 31 16:35:21 INT-MOVIL -- MARK --
Jul 31 16:39:04 INT-MOVIL racoon: INFO: IPsec-SA expired: ESP/Transport 195.55.47.10[0]->213.4.115.149[0] spi=214958394(0xcd0013a)
Jul 31 16:39:04 INT-MOVIL racoon: INFO: IPsec-SA expired: ESP/Transport 213.4.115.149[0]->195.55.47.10[0] spi=2019816514(0x7863f442)
Jul 31 16:42:34 INT-MOVIL racoon: INFO: purging ISAKMP-SA spi=52195d54c4ed8efc:cd39562018cd3064.
Jul 31 16:42:34 INT-MOVIL racoon: INFO: purged ISAKMP-SA spi=52195d54c4ed8efc:cd39562018cd3064.
Jul 31 16:42:35 INT-MOVIL racoon: INFO: ISAKMP-SA deleted 213.4.115.149[500]-195.55.47.10[500] spi:52195d54c4ed8efc:cd39562018cd3064
Jul 31 16:49:12 INT-MOVIL racoon: INFO: respond new phase 1 negotiation: 213.4.115.149[500]<=>195.55.47.10[500]
Jul 31 16:49:12 INT-MOVIL racoon: INFO: begin Identity Protection mode.
Jul 31 16:49:12 INT-MOVIL racoon: INFO: received Vendor ID: draft-ietf-ipsec-nat-t-ike-07
Jul 31 16:49:12 INT-MOVIL racoon: INFO: received Vendor ID: draft-ietf-ipsec-nat-t-ike-03
Jul 31 16:49:12 INT-MOVIL racoon: INFO: received Vendor ID: draft-ietf-ipsec-nat-t-ike-02
Jul 31 16:49:12 INT-MOVIL racoon: INFO: received Vendor ID: CISCO-UNITY
Jul 31 16:49:12 INT-MOVIL racoon: INFO: received Vendor ID: DPD
Jul 31 16:49:12 INT-MOVIL racoon: INFO: received Vendor ID: draft-ietf-ipsra-isakmp-xauth-06.txt
Jul 31 16:49:12 INT-MOVIL racoon: INFO: ISAKMP-SA established 213.4.115.149[500]-195.55.47.10[500] spi:52195d54bc249a03:6bbc775a9830d7c1
Jul 31 16:49:12 INT-MOVIL racoon: INFO: respond new phase 2 negotiation: 213.4.115.149[500]<=>195.55.47.10[500]
Jul 31 16:49:12 INT-MOVIL racoon: INFO: Update the generated policy : 195.55.47.10/32[0] 213.4.115.149/32[0] proto=any dir=in
Jul 31 16:49:12 INT-MOVIL racoon: INFO: IPsec-SA established: ESP/Transport 195.55.47.10[0]->213.4.115.149[0] spi=244423608(0xe919bb8)
Jul 31 16:49:12 INT-MOVIL racoon: INFO: IPsec-SA established: ESP/Transport 213.4.115.149[0]->195.55.47.10[0] spi=2905896494(0xad34762e)
Jul 31 16:49:12 INT-MOVIL racoon: ERROR: such policy does not already exist: "195.55.47.10/32[0] 213.4.115.149/32[0] proto=any dir=in"
Jul 31 16:49:12 INT-MOVIL racoon: ERROR: such policy does not already exist: "213.4.115.149/32[0] 195.55.47.10/32[0] proto=any dir=out"
Jul 31 16:51:04 INT-MOVIL racoon: INFO: IPsec-SA expired: ESP/Transport 195.55.47.10[0]->213.4.115.149[0] spi=214958394(0xcd0013a)
Jul 31 16:51:04 INT-MOVIL racoon: INFO: IPsec-SA expired: ESP/Transport 213.4.115.149[0]->195.55.47.10[0] spi=2019816514(0x7863f442)
Jul 31 17:04:34 INT-MOVIL racoon: INFO: IPsec-SA expired: ESP/Transport 195.55.47.11[0]->213.4.115.149[0] spi=73088254(0x45b3cfe)
Jul 31 17:04:34 INT-MOVIL racoon: INFO: IPsec-SA expired: ESP/Transport 213.4.115.149[0]->195.55.47.11[0] spi=2708717587(0xa173c013)
Jul 31 17:07:23 INT-MOVIL racoon: INFO: purging ISAKMP-SA spi=958e7c04ab6d373c:5fd3b0446c66cb7f.
Jul 31 17:07:23 INT-MOVIL racoon: INFO: purged ISAKMP-SA spi=958e7c04ab6d373c:5fd3b0446c66cb7f.
Jul 31 17:07:24 INT-MOVIL racoon: INFO: ISAKMP-SA deleted 213.4.115.149[500]-195.55.47.11[500] spi:958e7c04ab6d373c:5fd3b0446c66cb7f
Jul 31 17:13:13 INT-MOVIL racoon: INFO: respond new phase 1 negotiation: 213.4.115.149[500]<=>195.55.47.11[500]
Jul 31 17:13:13 INT-MOVIL racoon: INFO: begin Identity Protection mode.
Jul 31 17:13:13 INT-MOVIL racoon: INFO: received Vendor ID: draft-ietf-ipsec-nat-t-ike-07
Jul 31 17:13:13 INT-MOVIL racoon: INFO: received Vendor ID: draft-ietf-ipsec-nat-t-ike-03
Jul 31 17:13:13 INT-MOVIL racoon: INFO: received Vendor ID: draft-ietf-ipsec-nat-t-ike-02
Jul 31 17:13:14 INT-MOVIL racoon: INFO: received Vendor ID: CISCO-UNITY
Jul 31 17:13:14 INT-MOVIL racoon: INFO: received Vendor ID: DPD
Jul 31 17:13:14 INT-MOVIL racoon: INFO: received Vendor ID: draft-ietf-ipsra-isakmp-xauth-06.txt
Jul 31 17:13:14 INT-MOVIL racoon: INFO: ISAKMP-SA established 213.4.115.149[500]-195.55.47.11[500] spi:958e7c04b33f83ae:af432d76c23664fc
Jul 31 17:13:14 INT-MOVIL racoon: INFO: respond new phase 2 negotiation: 213.4.115.149[500]<=>195.55.47.11[500]
Jul 31 17:13:14 INT-MOVIL racoon: INFO: Update the generated policy : 195.55.47.11/32[0] 213.4.115.149/32[0] proto=any dir=in
Jul 31 17:13:14 INT-MOVIL racoon: INFO: IPsec-SA established: ESP/Transport 195.55.47.11[0]->213.4.115.149[0] spi=121149130(0x73896ca)
Jul 31 17:13:14 INT-MOVIL racoon: INFO: IPsec-SA established: ESP/Transport 213.4.115.149[0]->195.55.47.11[0] spi=1711717523(0x6606bc93)
Jul 31 17:13:14 INT-MOVIL racoon: ERROR: such policy does not already exist: "195.55.47.11/32[0] 213.4.115.149/32[0] proto=any dir=in"
Jul 31 17:13:14 INT-MOVIL racoon: ERROR: such policy does not already exist: "213.4.115.149/32[0] 195.55.47.11/32[0] proto=any dir=out"
Jul 31 17:16:34 INT-MOVIL racoon: INFO: IPsec-SA expired: ESP/Transport 195.55.47.11[0]->213.4.115.149[0] spi=73088254(0x45b3cfe)
Jul 31 17:16:34 INT-MOVIL racoon: INFO: IPsec-SA expired: ESP/Transport 213.4.115.149[0]->195.55.47.11[0] spi=2708717587(0xa173c013)
Jul 31 17:17:01 INT-MOVIL /USR/SBIN/CRON[2116]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

---

