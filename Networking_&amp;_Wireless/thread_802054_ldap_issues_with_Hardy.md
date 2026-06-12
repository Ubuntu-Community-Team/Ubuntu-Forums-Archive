---
title: "ldap issues with Hardy"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by Pierrewiet on 2008-05-21
I installed ldap according to [https://help.ubuntu.com/community/SingleSignOn](https://help.ubuntu.com/community/SingleSignOn) and created my own tls/ssl certificate as decsribed.

When testing the ssl setup with "openssl s_client -connect SERVER-NAME:636 -showcerts - state" I get following message back:

CONNECTED(00000003)
SSL_connect:before/connect initialization
SSL_connect:SSLv2/v3 write client hello A
5352:error:140790E5:SSL routines:SSL23_WRITE:ssl handshake failure:s23_lib.c:188:

How can this happen? And more important: how can I get a working setup of ldap with ssl?

Thanks in advance.

---

### Post by lavicky on 2008-11-24
Same problem on 8.04 LTS as well as on JeOS virtual server. Nobody solve it yet? Thanks for info.

---

