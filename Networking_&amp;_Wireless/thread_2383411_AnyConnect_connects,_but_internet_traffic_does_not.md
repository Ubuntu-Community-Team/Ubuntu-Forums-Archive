---
title: "AnyConnect connects, but internet traffic does not route through the VPN"
date: 2018-01-24
forum: Networking &amp; Wireless
---

### Post by Blnd2Spll on 2018-01-24
I am using Ubuntu 16.04, and trying to connect to a VPN via Cisco Anyconnect 3.1.0742. Regardless of if I use the Anyconnect GUI or use openconnect via command line, I have the same problem: I'm able to connect to the VPN and login without issue, and it says I'm connected, but none of my internet traffic is being re-routed through the VPN. That is, if I check my IP, it still give my actual IP rather than my VPN host IP.

Specifically, openconnect gives:

```

Login with your ID and password
Username:
Password:
Password:
POST https*****
Got CONNECT response: HTTP 1.1 200 OK
CSTP connected. DPD 30, Keepalive 30
Connected tun0 as 172.23.97.114, using SSL
Established DTLS connection (using GnuTLS). Ciphersuite (DTLS0.9)-(RSA)-(AES-128-CBC)-(SHA1).
```

And it waits here without issue until I close it. AnyConnect GUI works as normal. But at no time is my internet apparently running through the VPN.


This was working fine for me a month or two ago, but has since stopped working. Any thoughts on how to trouble shoot this?

---

