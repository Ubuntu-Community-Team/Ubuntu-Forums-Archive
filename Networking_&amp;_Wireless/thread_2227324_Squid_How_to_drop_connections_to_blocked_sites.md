---
title: "Squid: How to drop connections to blocked sites"
date: 2014-06-01
forum: Networking &amp; Wireless
---

### Post by maxxjr on 2014-06-01
I have configured squid to successfully block specific sites, via something like

http_access deny bad_url

When Firefox tries to access one of these blocked sites, an error message is returned to the user that the proxy server is refusing the connection.  Is there a way to set up squid so that there is no response (so that the browser would timeout)?

---

