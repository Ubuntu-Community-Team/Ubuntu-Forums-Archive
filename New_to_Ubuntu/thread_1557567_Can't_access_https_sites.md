---
title: "Can't access https sites"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by blairm on 2010-08-20
Hi,

Having trouble with wireless - everything works fine until I try to log in to any https site. The computer sits there and thinks for a while, before giving me the following message:

[B]The connection was interrupted
[/B]The connection to [www.google.com](www.google.com) was interrupted while the page was being loaded
- The site could be temporarily unaailable or too busy. Try again in a few moments. (get the same result).
- If you are unable to load any pages check your computer's network connection (it's just https pages I have trouble with)
- If your computer or network is protected by a firewall or proxy, make sure that Firefox is permitted to access the web (did sudo ufw disable, as suggested in a thread here, and made no difference).

EDIT: Have discovered that I can access these sites by allowing all incoming and all outgoing connections in gufw, but not sure that's a good idea long-term - wouldn't that pose a security risk?

Cheers,

Blair

---

### Post by lovinglinux on 2010-08-21
> **blairm said:**
> EDIT: Have discovered that I can access these sites by allowing all incoming and all outgoing connections in gufw, but not sure that's a good idea long-term - wouldn't that pose a security risk?

Cheers,

Blair

Have you tried to disable ipv6? See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

About the firewall, most likely that you don't even need it. Check [these threads]("http://tinyurl.com/252s7wq") for explanations.

---

