---
title: "Help Postfix LDAP"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by Deme János on 2007-05-21
I'd like to use postfix-ldap, with Win2003 AD, but if I'm connecting, it says:

postmap -q deme ldap:/etc/postfix/ldap-aliases.cf
...
dict_ldap_connect: Unable to bind server ... :49 (Invalid Credentials)

With openldap client, I can connect with the option -x.

I think it'd like to connect with sasl, but i dont now how to turn it off.

Thanks for any help!

---

