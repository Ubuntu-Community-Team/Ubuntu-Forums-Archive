---
title: "Internet Sharing works, except for firefox in ubuntu"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by justin75 on 2008-10-04
First off, I had internet sharing working last week, thanks to this
[http://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing](http://help.ubuntu.com/community/Internet/ConnectionSharing?action=show&redirect=InternetConnectionSharing)
and another ubuntuforums.org thread (which i don't have the link)

 but after restarting the internet connected computer, internet sharing stopped working. I tried reconfiguring everything on my host and client computers, then finally tried using konqueror to connect to the internet and it worked! but firefox on the same (kubuntu) computer still will not connect. it did last week.

Firefox on the windows machine works great, but  firefox on the kubuntu machine that no longer connects. actually apt-get does not connect either, but konqueror does.

what am i missing?

tia
:)

---

### Post by itsjareds on 2008-10-04
Did you set a proxy for Windows, or a dead proxy on Firefox (on Ubuntu)?

Maybe you should change your DNS settings - what does it say in the status bar when FF wants to connect?

---

### Post by justin75 on 2008-10-04
I did not set a proxy in Windows, nor kubuntu.

the status bar in firefox reads: looking up google.com .. then:  done

---

### Post by itsjareds on 2008-10-04
Have you tried typing in an IP, such as [64.233.187.99]("64.233.187.99") (google.com)?

---

### Post by justin75 on 2008-10-04
Ah ha!

that worked. so what does that mean?

---

### Post by itsjareds on 2008-10-04
That just means you need to change or set DNS servers. These are what converts domain names (such as google.com) to IP addresses (such as 64.233.187.99).

Open up nm-applet (System > Administration > Network), unlock it, and then go to the DNS tab. Either put your DNS server (if you know it) or put in OpenDNS's server. I use OpenDNS and I really like it. Haven't had any problems with it.

Add in these two OpenDNS servers for your DNS servers:
```
208.67.220.220
208.67.222.222
```

After this, you should be able to use Firefox :)

---

### Post by justin75 on 2008-10-04
i'm not sure about changing to the openDNS servers- might there be some conquences? (speed? other?)

besides, it was working last week with my isp's nameservers. :/

---

### Post by itsjareds on 2008-10-04
Oh. I'm not saying you have to completely switch, I'm just asking you to do it to see if that is the problem :D

If that works just change the DNS servers to your ISP's.

---

### Post by justin75 on 2008-10-05
changing the DNS servers didn't help.

however, now I know it's not related to the internet sharing because I tried connecting directly to the internet and got the same problem. been banging my head against the wall for far too long now... i could just reinstall everything, but that's so frustrating when I know it must be a simple config setting somewhere.

---

### Post by itsjareds on 2008-10-05
I'm not sure what to tell you then, all I really know is that if you can connect by IP but not by domain, it should be a problem with DNS servers. (but I'm not that experienced ;))

---

