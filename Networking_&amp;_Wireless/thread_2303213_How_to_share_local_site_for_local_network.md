---
title: "How to share local site for local network?"
date: 2015-11-17
forum: Networking &amp; Wireless
---

### Post by andrey34 on 2015-11-17
Hello every body, can you tell me please how can I share my local site to have access for all users from one route connection?

---

### Post by Lars Noodén on 2015-11-17
If you mean a web site using Apache2, then you want to look at [allow](http://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#allow) and [deny](http://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#deny) directives for your site.    You might also look at complimenting that with some UFW rule to allow only from the one subnet.

---

