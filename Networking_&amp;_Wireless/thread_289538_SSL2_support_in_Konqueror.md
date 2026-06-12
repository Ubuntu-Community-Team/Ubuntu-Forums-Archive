---
title: "SSL2 support in Konqueror"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by ehamberg on 2006-10-31
To use my university's wireless network I need to authenticate with a webauth service. After upgrading to Edgy I can't get this to work with Konqueror anymore.
Konqueror will just tell me "Could not connect to host webauth1.ntnu.no.", while Firefox is a bit more helpful and tells me that it can't connect to the website because it uses an old, insecure version of SSL.
To get it to work I have to set these two config variables to **true**:
security.ssl2.rc4_128
security.enable_ssl2

How can I do the same for KDE/Konqueror?

---

