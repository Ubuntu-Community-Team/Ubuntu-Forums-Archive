---
title: "Can't connect via wireless"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by stukid on 2009-08-12
Brand new Dell mini 9 with Ubuntu 8.04.1.
I cannot access web via wireless. Wired is fine.
Dell tech support says its my router settings incompatible with Ubuntu, but everything else works- PC's, macs, IPODs, wii, etc.
When I enter WEP code, it cannot connect!

---

### Post by MyR on 2009-08-12
> **stukid said:**
> When I enter WEP code, it cannot connect!

Welcome to the forums & Ubuntu!

Not to burst your bubble, but WEP is completely insecure; consider to switching to WPA.

If you *must* use WEP, what model router do you have?

peace

---

### Post by Bachstelze on 2009-08-12
> **MyR said:**
> Not to burst your bubble, but WEP is completely insecure; consider to switching to WPA.

[Not to burst your bubble...](http://arstechnica.com/security/news/2008/11/wpa-cracked.ars)

Keep it on-topic please.

---

### Post by MyR on 2009-08-12
> **HymnToLife said:**
> [Not to burst your bubble...](http://arstechnica.com/security/news/2008/11/wpa-cracked.ars)
From the article: "the security solution, simple: switch to AES-only in WPA2"

But of course I didn't go into too much detail because I was trying to:

> **HymnToLife said:**
> Keep it on-topic

In any event, switching the router to WPA is a potential solution to his/her problem.

---

### Post by mapes12 on 2009-08-13
> **stukid said:**
> Brand new Dell mini 9 with Ubuntu 8.04.1.
I cannot access web via wireless. Wired is fine.
Dell tech support says its my router settings incompatible with Ubuntu, but everything else works- PC's, macs, IPODs, wii, etc.
When I enter WEP code, it cannot connect!Are Dell saying that your wifi adapter has been tested by them and works with the version of Ubu you have installed. Let's have a look at it for you. If it's an internal adapter Applications>Accessories>Terminal ```
lspci
```then copy and paste the output back here.

---

### Post by MyR on 2009-08-13
> **mapes12 said:**
> Are Dell saying that your wifi adapter has been tested by them and works with the version of Ubu you have installed. Let's have a look at it for you. If it's an internal adapter Applications>Accessories>Terminal ```
lspci
```then copy and paste the output back here.

Some of the Dell minis come with Ubuntu pre-installed (yay!).  So I would assume that Dell made sure the WiFi was working before they sent them out the door.

---

