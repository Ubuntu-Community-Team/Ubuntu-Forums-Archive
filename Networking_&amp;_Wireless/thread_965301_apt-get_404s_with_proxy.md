---
title: "apt-get 404s with proxy"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by Earl_Maroon on 2008-10-31
When I try to use apt-get I get 404s. I believe it is in some way connected to my proxy settings, but I have no idea how to fix it. I did get 403s with Synaptic, but I added my proxy settings for that and that was fine. However, I'd like to be able to use the command line and I don't know how to configure apt-get. Can anybody please help me?

---

### Post by Earl_Maroon on 2008-10-31
I worked it out by piecing together the information from a couple of other threads. I don't know how to delete this thread.

What worked was the command:
```
export http_proxy="[Proxy address:port]"
```
and that was it. The thread I had looked at previously omitted the quotes.
(Replace the square brackets with your proxy details.

---

