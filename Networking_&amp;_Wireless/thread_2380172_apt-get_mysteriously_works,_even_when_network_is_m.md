---
title: "apt-get mysteriously works, even when network is misconfigured"
date: 2017-12-14
forum: Networking &amp; Wireless
---

### Post by timothylegg on 2017-12-14
Hello,

I'm servicing a headless box buried deep inside an obfuscated tangle of misconfigured IT infrastructure that I don't have full authority over.  Yesterday, while installing a security patch on a piece of manually configured software, I discovered that outbound requests on port 80 and port 22 were refused (amongst many others), rendering tools such as scp, ssh, links and wget unasable.  That is a seperate issue that we are working on solving, but I am currently still collecting symptoms to help us lead to the root cause.

For a moment, I forgot the environment I was in and ran

# apt-get update ; apt-get upgrade

and it appeared to work normally.  I immediately realized what had happened and suspected that they had just fixed the problem, but found that ports 80 and 22 were still blocked.  I looked in the /etc/sources.list and verified that the sources prefixed with http.  Performing a links command I was not able to connect with the server address in that file (i.e.  [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu))

So how does apt-get work?  All these years, I imagined it was a script calling a bunch of wget over port 80.  Is that true?  To me, this is akin to seeing one street lamp inexplicably lit up amidst a city-wide power outage.

Thanks

---

