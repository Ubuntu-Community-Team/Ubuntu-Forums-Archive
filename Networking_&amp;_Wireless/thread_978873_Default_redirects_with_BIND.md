---
title: "Default redirects with BIND"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by boupartac on 2008-11-11
Hi all,

We buy a lot of domain names and I would like to know if this is possible:

1. When we buy a domain name, we provide our dns addresses as usual
2. __As soon__ as the address is registered, I would like web requests to this domain name to be redirected to our main website, say, [www.abc.com](www.abc.com), WITHOUT creating the dns zone at first.

Since we have a lot of web traffic, doing this would avoid users to have a "page not found" and we would get more traffic. The dns zone would be created shortly after that.

In fact, what I want is to add a "default http action" to bind and redirect them it [www.abc.com](www.abc.com). Is that possible?

I am using Bind 9.3.4.

Thanks for you help,

boupartaC

---

