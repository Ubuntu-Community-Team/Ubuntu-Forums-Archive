---
title: "How to set empty password for Samba 4 AD user?"
date: 2013-09-26
forum: Networking &amp; Wireless
---

### Post by ercling-gmail on 2013-09-26
Hello!

I am created user 'student'. Then set --min-pwd-length=0. In smb.cong in [global] section added 'null passwords = yes'.

I tried to change password via RSAT on Windows 7. After that, i can't login with empty password.

With ```
samba-tool user setpassword student
``` I can't insert empty password. 

How can I do that?


P.S: ubuntu server 12.04.3 amd64
samba 4.0.9 building from sources

---

