---
title: "Can I allow ads everywhere except for 2 websites using hosts file?  What's possible?"
date: 2018-12-06
forum: Networking &amp; Wireless
---

### Post by MechaMechanism on 2018-12-06
I don't use an ad-blocker.  In fact I don't use any method for blocking ads at all.  I'm subjected to ads daily.  There are two websites that I want to block ads on.  Only two websites.  I want to see ads on every other website.  These two websites use third-party ad networks.  Can I use the hosts file to only allow connections from those two domains and reject all other URLs coming from those two domains.  Is that possible?  I use these websites daily.  Please don't suggest I use another website, one of them is my hometown newspaper.  The local paper I absolutely need access too, and the other I suppose I could replace, but then, where would the sense of victory be over the ad network.

---

### Post by freemedia2018 on 2018-12-06
Add this to the bottom of your hosts file:

```
127.0.0.1 name-of-first-ad-website
127.0.0.1 name-of-second-ad-website
```

Remove http:// or https:// from the url and anything after .net .com, etc. so [www.notarealadwebsite.com]("http://www.notarealadwebsite.com") is fine, but lose the https:// (note, that does not go to a real website.)

---

### Post by MechaMechanism on 2018-12-07
> **freemedia2018 said:**
> Add this to the bottom of your hosts file:

```
127.0.0.1 name-of-first-ad-website
127.0.0.1 name-of-second-ad-website
```

Remove http:// or https:// from the url and anything after .net .com, etc. so [www.notarealadwebsite.com]("http://www.notarealadwebsite.com") is fine, but lose the https:// (note, that does not go to a real website.)

Great, thank you!

---

