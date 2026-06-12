---
title: "Conflict??: Privoxy+Hosts File+Addblock Plus. (overkill maybe )"
date: 2010-07-10
forum: New to Ubuntu
---

### Post by UbuNoob001 on 2010-07-10
Good day all, 
   I have done a bit of research and cant figure any reason there would be a conflict. Perhaps overkill and perhaps blocking something I want, but..

**Q: can anyone see a reason why using Privoxy+Hosts File +Addblock (extension in FireFox) would inhibit the functioning/security/privacy of the other? **

    for example (this may be a very noob question) I assume (?) that any privacy issues of Addblock (looking up visited/add sites) would be passed also through privoxy and therefore not be a problem. 

   
Finally: I have seen a few different ways of setting up the Preference for Privoxy in Firefox (just for basic use) Does HTTP: Localhost   8118,    HTTPS: Localhost 8118 seem alright?  Note that 127.0.0.1 didn't work but "Localhost" does. 

   Thanks all!

---

### Post by k3lt01 on 2010-07-10
I can't see any problem with having the three together, I had it like this myself up until a couple of weeks ago and the only thing I found was it slowed my browsing down.

As for your 2nd question [check this out]("http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/").Bodhizazen has quite a bit of info on security so take a look at that page and also the rest of his blog. You may also check out his posts here on the forums for more info.

---

### Post by UbuNoob001 on 2010-07-10
> **k3lt01 said:**
> I can't see any problem with having the three together, I had it like this myself up until a couple of weeks ago and the only thing I found was it slowed my browsing down.

As for your 2nd question [check this out]("http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/").Bodhizazen has quite a bit of info on security so take a look at that page and also the rest of his blog. You may also check out his posts here on the forums for more info.


k3lt01, thanks for the reference! This is a silly noob question but: is Privoxy simply a software application for content filtering? Or is it forwarding my requests to a web proxy so that the sits I connect to don't know "who I am" (although obviously my ISP does)?

---

### Post by k3lt01 on 2010-07-10
From my understanding privoxy is a content filter as well as a privacy protector. The proxy is the computer privoxy is installed on, that is why privoxy is set to its own port number. Bodhizazen has a link in his blog to the privoxy site that has user documentation.

---

### Post by bodhi.zazen on 2010-07-11
I think using all three is over kill.

I used a hosts file for a while, but switched to Privoxy some time ago now.

Prioxy is a proxy server that runs on your localhost. Firefox then makes a request for a web page to Privoxy, Privoxy retrieves the information.

Privoxy has two features, the first is privacy and the second is adblocking and I like both.

Privoxy alone will not perform what most people term "content filtering", It will not block porn for example, just advertisements.

I personally use Dansguardian for content filtering.

I find Privoxy + Dansguardian takes less time and effort then maintaining a hosts file.

The Problem with Adblock Plus it that it only applies to Firefox.

Privoxy is very feature rich and I find I do not need a hosts file or AdblockPlus. I have minimal advertisement, about the same as with a hosts file or adblock plus.

[http://www.privoxy.org/user-manual/introduction.html](http://www.privoxy.org/user-manual/introduction.html)

HTH

---

### Post by UbuNoob001 on 2010-07-12
> **bodhi.zazen said:**
> I think using all three is over kill.

I used a hosts file for a while, but switched to Privoxy some time ago now.(...)

Prioxy is a proxy server that runs on your localhost. Firefox then makes a request for a web page to Privoxy, Privoxy retrieves the information.



[http://www.privoxy.org/user-manual/introduction.html](http://www.privoxy.org/user-manual/introduction.html)

HTH

Bodhi.zazen, (and others!) Thanks so much for commenting on my question. Its rather an honor as I have been enjoying your stickies as they have helped me learn quite a bit! Thanks again for all you do.

---

### Post by bodhi.zazen on 2010-07-12
> **UbuNoob001 said:**
> Bodhi.zazen, (and others!) Thanks so much for commenting on my question. Its rather an honor as I have been enjoying your stickies as they have helped me learn quite a bit! Thanks again for all you do.

:redface: 

Glad you found the insights of the community helpful.

---

