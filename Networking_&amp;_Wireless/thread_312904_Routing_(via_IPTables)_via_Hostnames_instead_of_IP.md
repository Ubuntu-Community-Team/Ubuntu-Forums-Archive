---
title: "Routing (via IPTables) via Hostnames instead of IP"
date: 2006-12-05
forum: Networking &amp; Wireless
---

### Post by ricadelic on 2006-12-05
Hi,

I've got a situation where the proxy server at work only allows port 80 and 443 outgoing. ISS only allows an SSL conenction on port 443.

Since i've got SSH and HTTPS services i've got a problem since both needs to be flowing through port 443.

Now i've setup mydomain.com and i've setup some aliasses like ssh.mydomain.com and [www.mydomain.com](www.mydomain.com). Both have the same IP.

Is it somehow possible to redirect anything thats coming in from ssh.mydomain.com:443 and route it to internal:22 via iptables?

same for [www.mydomain.com:443](www.mydomain.com:443) to internal:443 via iptables.

Anyone knows if it's anyhow possible via a local DNS server or something? 

Please let me know if you need more information.

Cheers,
rick

---

### Post by rbalfour on 2006-12-05
> **ricadelic said:**
> Hi,

I've got a situation where the proxy server at work only allows port 80 and 443 outgoing. ISS only allows an SSL conenction on port 443.

Since i've got SSH and HTTPS services i've got a problem since both needs to be flowing through port 443.

Now i've setup mydomain.com and i've setup some aliasses like ssh.mydomain.com and [www.mydomain.com](www.mydomain.com). Both have the same IP.

Is it somehow possible to redirect anything thats coming in from ssh.mydomain.com:443 and route it to internal:22 via iptables?

same for [www.mydomain.com:443](www.mydomain.com:443) to internal:443 via iptables.

Anyone knows if it's anyhow possible via a local DNS server or something? 

Please let me know if you need more information.

Cheers,
rick

you could always look into OpenVPN for get pass the proxy. Create a VPN from you work machine to your server then tunnel all traffic thru that. Works like a charm.

---

