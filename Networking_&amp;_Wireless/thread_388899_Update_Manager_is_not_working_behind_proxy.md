---
title: "Update Manager is not working behind proxy"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by behrangsa on 2007-03-20
Hi,

My notebook is behind an authenticated proxy. I have configured Synaptics to go through the proxy so it works fine. But the Update Manager is not working. How can I force update manager to go through the proxy?

Also, what should I do to make the apt-get go through the proxy as well?

Regards,
Behi

---

### Post by flossgeek on 2007-03-20
type this into command line for apt-get:-

```
export http_proxy=&#8221;http://user:pass@youProxyAddress:port/&#8221;
```

This will enable apt-get to work through a proxy in your logged in session.

---

