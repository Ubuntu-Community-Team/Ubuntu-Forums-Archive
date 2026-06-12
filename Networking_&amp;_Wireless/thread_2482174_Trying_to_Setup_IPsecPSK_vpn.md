---
title: "Trying to Setup IPsec/PSK vpn"
date: 2022-12-22
forum: Networking &amp; Wireless
---

### Post by calgrainger on 2022-12-22
Hey Hey

As the title says im trying to connect to my work VPN which is an IPsec/PSK config. I have attempted to connect using StrongSwan and worked my way through the issues there in, and saw a post suggesting i switch to libreswan which i did. With libreswan i hit an error where it was not accepting ikev1 so i added ikev1-policy=accept to the conf, however after doing so and rebooting (for the heck of it) its still failing to connect to my VPN. I can see the handshakes taking place and it can successfully ping my VPNs IP however after it attempts to keepalive i can see the following:

ignoring informational payload NO_PROPOSAL_CHOSEN, msgid=00000000, length=64
003 "96f8def5-a03d-46b2-b462-9a6bc8b3c7de" #1: received and ignored notification payload: NO_PROPOSAL_CHOSEN

followed by:

nm-l2tp[8184] <warn>  Timeout trying to establish IPsec connection
nm-l2tp[8184] <info>  Terminating ipsec script with PID 8488.
nm-l2tp[8184] <warn>  Could not establish IPsec tunnel.

Hoping someone is able to help me as my VPN is crucial when im working for home. I can provide the output of my debug cmd if needed

Thanks in advance

Cal

---

