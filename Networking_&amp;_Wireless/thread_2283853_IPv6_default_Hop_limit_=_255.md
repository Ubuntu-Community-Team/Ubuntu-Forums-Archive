---
title: "IPv6 default Hop limit = 255?"
date: 2015-06-25
forum: Networking &amp; Wireless
---

### Post by richard51 on 2015-06-25
I am setting up a Ubuntu box as an IPv6 router, using ip6tables. According to **RFC 4890**, address configuration and router selection messages must be received with a hop limit = 255.

**Questions:**

[LIST=1]
[*]                         Isn't the default hop limit on a Ubuntu host set to 64? 
[*]                         Does the hop limit get set automatically to 255 for address configuration and router selection messages? 
[*]Am I OK checking that the hop limit is 255 using ip6tables (-m hl --hl-eq 255) to determine address configuration and router selection messages? 
[/LIST]

---

