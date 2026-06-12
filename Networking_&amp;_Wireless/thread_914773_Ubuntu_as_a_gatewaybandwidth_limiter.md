---
title: "Ubuntu as a gateway/bandwidth limiter"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by Mr Green on 2008-09-09
I recently got a tenant in my house, and beeing the good guy that I am I allow her to use my internet connection. My problem is that she is constantly downloading stuff over different p2p applications making the connection very slow. I have a webserver running and I need to be sure that it has available bandwidth when people access it.

What I would like to do is put up a linuxbox between the adsl modem and the wireless router which gives her access, so that I could get some control over the bandwidth she(or any wireless client) can utilize, or control which protocols have priority. If I could be sure that http traffic had priority it would not be a problem.

I'm hoping someone can point me in the right direction for a well known approach for this scenario. I really hope that I can use Ubuntu though as I really love it and know it pretty well after using it since 6.04.


Any help is highly appreciated.

Best answer will be rewarded $20 at Full Tilt Poker.

---

### Post by ilrudie on 2008-09-09
[Linux Advanced Routing & Traffic Control]("http://lartc.org/")

or

[here]("http://ubuntuforums.org/showthread.php?t=900646")

---

### Post by Cmndr Hippofiralkus on 2008-09-09
a better suggestion is to ask her to refrain from such heavy usage

---

### Post by ilrudie on 2008-09-09
> **Cmndr Hippofiralkus said:**
> a better suggestion is to ask her to refrain from such heavy usage

I disagree.  With simple traffic shaping I have been able to keep browsing and interactive traffic flowing smoothly and quickly while still downloading at 95% of my connections capacity.  It is not all that difficult to set up.  I set it up in my dd-wrt router but any iproute2/tc capable linux distro should do.

---

### Post by Mr Green on 2008-09-10
> **ilrudie said:**
> [Linux Advanced Routing & Traffic Control]("http://lartc.org/")

or

[here]("http://ubuntuforums.org/showthread.php?t=900646")

Thanks a lot ilrudie.

Great article, really interesting and helpful. PM me if you have a ftp account and want your 20 bucks worth of helpful cash.

Now I can't wait to get down and dirty with this.

---

