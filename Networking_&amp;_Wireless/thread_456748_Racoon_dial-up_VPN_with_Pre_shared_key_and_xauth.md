---
title: "Racoon dial-up VPN with Pre shared key and xauth"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by bence8810 on 2007-05-28
Hi

I am trying to connect to a Netscreen VPN box with Racoon. My ipsec-tools is at ver 0.6.6

If there is only a pre-shared key for authentication, I can connect without a problem. However I need to have psk and xauth together, and I cannot change that scenarrio.

With only psk, in the racoon.conf I have this:

```
authentication_method pre_shared_key;
```

What do I need instead of that when needing psk and xauth thereafter?

I found some pages referring to something like this:

```
xauth_psk_client
```

But I am unsure if that is what I need, and also I dont have this as an option in my racoon.conf when I check the man page. 

Any help is appreciated,

Thanks

Ben

---

