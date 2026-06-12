---
title: "Is pihole and cloudflare working together?"
date: 2021-12-13
forum: Networking &amp; Wireless
---

### Post by lance bermudez on 2021-12-13
I used [https://docs.pi-hole.net/guides/dns/cloudflared/](https://docs.pi-hole.net/guides/dns/cloudflared/)  to set up pihole to work with cloudflare. 

However the [https://1.1.1.1/help](https://1.1.1.1/help) is saying
```

Using DNS over HTTPS (DoH)	No
Using DNS over TLS (DoT)	No

```

Also [https://www.cloudflare.com/ssl/encrypted-sni/](https://www.cloudflare.com/ssl/encrypted-sni/) browser check has
```

? Secure DNS 
and checks for DNSSEC and TLS 1.3. 

```

Pihole has Upstream DNS Servers 127.0.0.1#5053
I also have Use DNSSEC checked

---

