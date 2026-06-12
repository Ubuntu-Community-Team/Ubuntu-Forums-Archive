---
title: "ip address"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by vagelism on 2009-01-14
HELLO TO ALL.

How I can add a static ip , mask and gateway , and dns....to an interface via console?
Thank you.

---

### Post by albinootje on 2009-01-14
> **vagelism said:**
>  How I can add a static ip , mask and gateway , and dns....to an interface via console?


Check : 
```

man interfaces

```
And here :
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

For DNS you would have to edit /etc/resolv.conf although your nameservers might be already in there if you've requested an ip-address through DHCP already.

---

