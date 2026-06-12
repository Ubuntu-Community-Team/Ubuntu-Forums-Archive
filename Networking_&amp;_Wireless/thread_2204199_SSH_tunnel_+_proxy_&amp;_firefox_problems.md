---
title: "SSH tunnel + proxy &amp; firefox problems"
date: 2014-02-07
forum: Networking &amp; Wireless
---

### Post by Wrbhhh on 2014-02-07
I'm using my computer in a company with really complicated networking. For surfing the web we need to use a proxy (www.proxy.server) or else we can't get out of our intranet.

But also, I'd like to access one web application on one server (www.application.server) within our network. Application's port isn't open to the outside, but the SSH port is. So I created a SSH tunnel like this:

```
ssh -fNL 8247:127.0.0.1:8247 www.application.server
```

This is my /etc/enviroment file:

```
PATH="bla...bla...not...important..."
http_proxy="http://www.proxy.server:8080"
https_proxy="http://www.proxy.server:8080"
ftp_proxy="http://www.proxy.server:8080"
no_proxy="localhost, 127.0.0.1"
```

I have Kubuntu installed and in it's network settings I have "use system proxy configuration" selected. In Firefox's proxy settings I have "use system proxy settings" selected.

When I try to wget my URL, everything works:
```
wget http://127.0.0.1:8247/
```

But when I try to open the exact same URL in Firefox, it doesn't work, I get a timeout. And I see Firefox is trying to get this URL through the proxy, although it shouldn't according to my configuration.

Why? :(


**EDIT:**

I've also tried to open my URL in rekonq. In it everything works fine as well, like with wget. So it has to be something in Firefox.


**EDIT2:**

Ok, I resolved it. The problem was a cached 301 redirect. I opened the history sidebar and chose to forget my link and now everything works fine. Ah....

---

