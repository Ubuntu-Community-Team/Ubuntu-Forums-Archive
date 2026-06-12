---
title: "Any risk on modifying /usr/lib/proxychains3/proxyresolv like this?"
date: 2020-06-27
forum: Networking &amp; Wireless
---

### Post by finznc on 2020-06-27
I had misunderstand the article and I had changed the line of  proxyresolv from `DNS_SERVER=${PROXYRESOLV_DNS:-4.2.2.2}` to `DNS_SERVER=8.8.8.8`, the `proxychains` still worked but any risk?

---

### Post by dino99 on 2020-06-27
Get the story: [https://www.tummy.com/articles/famous-dns-server/](https://www.tummy.com/articles/famous-dns-server/)

---

### Post by finznc on 2020-06-28
Whats the difference between `DNS_SERVER=8.8.8.8` and `DNS_SERVER=${PROXYRESOLV_DNS:-8.8.8.8}`?

---

### Post by wildmanne39 on 2020-06-28
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

