---
title: "What DNS I'm using?"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by bangmalley on 2009-12-22
I just want to double check I'm not using my ISP DNS.
I'm using router. So, checking the setting only yield router IP.
Apparently, there's a website that tells what DNS i'm using, but I forgot the website, can't find it through google.

---

### Post by Grenage on 2009-12-22
If you are using router DHCP, then you'll be using whatever the router is.  Unless you specified a custom DNS on the router, you'll be using your ISP's DNS.

Assuming all that is false and you manually set it all locally:

If you specified an alternate one:

```
nslookup google.com
```

You should get the DNS server you are using:

```
Server:         192.168.100.63
```

---

### Post by coffeecat on 2009-12-22
> **Grenage said:**
> If you are using router DHCP, then you'll be using whatever the router is.  Unless you specified a custom DNS on the router, you'll be using your ISP's DNS.

You can specify what DNS servers to use in Network Manager to override whatever the router wants to get up to. I found that useful in replacing the always-slow DNS servers of my ISP with the open DNS ones.

@bangmalley, right-click on the network manager icon and choose 'Connection Information'. They're listed there.

---

