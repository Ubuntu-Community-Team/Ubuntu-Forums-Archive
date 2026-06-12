---
title: "How to load balance SOCKS5 proxies ?"
date: 2017-01-26
forum: Networking &amp; Wireless
---

### Post by hillzone1 on 2017-01-26
I have some socks proxies that I created with:
```
ssh -D 1080
ssh -D 1081
ssh -D 1082
```
And I need to load balance those proxies so that when one dies it'll automatically switch to another one, is there a way to do that ?

---

### Post by hillzone1 on 2017-01-27
anyone ?

---

### Post by 1clue on 2017-01-27
I don't think so.

I'm no expert on this, but I believe each of those ssh commands will be its own session, and as such they won't be interchangeable.

---

