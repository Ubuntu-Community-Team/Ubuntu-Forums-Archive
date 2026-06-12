---
title: "How safe is SCP over internet"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by RichardCL on 2010-01-18
Dear Forum,

How safe is it if I create a port forward from example.com:XXXX to weberverIP:22 in my hardware router (Fritz Box)?

I want to be able to publish to the web using WinSCP via internet (DynDNS).

FTP is not installed on the webserver at all. Not even anon. Only a fresh LAMP sever installation of Karmic.

I can FTP via SSH using winSCP over the internal network fine. I still use a password but may move to key files, when I work out how and have time.

There is no data I really care about on the webserver but there is on my Ubuntu desktop (LAN connected to the webserver).

Should I be setting up a VPN?

Many thanks


Rich

---

### Post by [S2] on 2010-01-18
> **RichardCL said:**
> Dear Forum,

How safe is it if I create a port forward from example.com:XXXX to weberverIP:22 in my hardware router (Fritz Box)?

very safe. traffic is encrypted and nothing is sent in cler text. go ahead!

---

