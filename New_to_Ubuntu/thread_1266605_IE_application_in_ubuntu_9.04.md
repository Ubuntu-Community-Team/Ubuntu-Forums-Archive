---
title: "IE application in ubuntu 9.04"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by k66473 on 2009-09-14
Hi 

There are some websites (bank) requires IE to do the transaction. 
I try to look for IE tab add on for Firefox but unfortunately, it does not support for Firefox in ubuntu.

Do you have any advices or ideas to bit this situation?

Regards.

---

### Post by DougieFresh4U on 2009-09-14
> **k66473 said:**
> Hi 

There are some websites (bank) requires IE to do the transaction. 
I try to look for IE tab add on for Firefox but unfortunately, it does not support for Firefox in ubuntu.

Do you have any advices or ideas to bit this situation?

Regards.
IE4Linux ???
[http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.tatanka.com.br%2F&ei=WOeuSuH8Bd2J8QbxmJDHCA&usg=AFQjCNF1jEBrRDSsbWwAxQ93UualUPrAbw&sig2=q1WdeRv9b8OqZLx5N5t3Gw](http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwww.tatanka.com.br%2F&ei=WOeuSuH8Bd2J8QbxmJDHCA&usg=AFQjCNF1jEBrRDSsbWwAxQ93UualUPrAbw&sig2=q1WdeRv9b8OqZLx5N5t3Gw)

---

### Post by louisr on 2009-09-18
You can try faking the user-agent in firefox to make it look like you're running IE. The page may be distorted however or not work if certain plugins are required.

In firefox:

enter about:config
right click > New > string
name: general.useragent.override
value: Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 5.1)

---

