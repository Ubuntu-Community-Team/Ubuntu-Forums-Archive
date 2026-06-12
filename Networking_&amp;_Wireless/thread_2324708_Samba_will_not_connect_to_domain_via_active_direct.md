---
title: "Samba will not connect to domain via active directory"
date: 2016-05-15
forum: Networking &amp; Wireless
---

### Post by alex422 on 2016-05-15
Hi all

I am so close to being able to connect to my windows active directory.

I want to use the ubuntu server as a simple file server for domain users

When I do a kinit I can get a ticket but when I try to join the domain with net ads I get the following error, am literally pulling out hair trying to work out what is going on


```

root@tagelinux:/home/tage# net ads join -U tageadmin
Enter tageadmin's password:
gss_init_sec_context failed with [ Miscellaneous failure (see text): Message stream modified]
kinit succeeded but ads_sasl_spnego_gensec_bind(KRB5) failed: An internal error occurred.
Failed to join domain: failed to connect to AD: An internal error occurred.


```

Thank you in advance

---

