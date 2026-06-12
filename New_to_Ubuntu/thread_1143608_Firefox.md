---
title: "Firefox"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by Duskao on 2009-04-30
Firefox seems to be slowing down. Not sure why exactly. I cleared my private data and don't use any add-on's. I did use synaptic and clicked the "mark all upgrades" box and firefox was one of the things that was upgraded. Was that a mistake? Should I try to uninstall and reinstall it?

Seems like it keeps taking longer to "look up" sites.

---

### Post by nandemonai on 2009-04-30
> **Duskao said:**
> Firefox seems to be slowing down. Not sure why exactly. I cleared my private data and don't use any add-on's. I did use synaptic and clicked the "mark all upgrades" box and firefox was one of the things that was upgraded. Was that a mistake? Should I try to uninstall and reinstall it?

Seems like it keeps taking longer to "look up" sites.

Sure it's not a connectivity issue rather than a browser one?

Latest version of FF running pretty sweet here (all be it still a massive memory hog).

---

### Post by Zeedok on 2009-04-30
I haven't had problems with FF in jaunty either.  There is no harm in reinstalling it though - but it may not fix your problem.  Just find firefox in synaptic, right click and mark for reinstallation.

Although any upgrade **_could_** break your system, they usually don't, so you've done nothing wrong by upgrading.  As the old hands on the forum would say though, if your system is "mission critical" and works fine, then don't touch . . .

I have just installed [Swiftfox]("http://getswiftfox.com/") which is a customised version of firefox especially for linux.  It seems faster, but I have to admit I had a few teething problems getting the flash and pdf plugins to work, but . . . I'm one of those people that doesn't mind sorting out a few issues after an update.  Sometimes linux is a love/hate relationship . . .

---

### Post by skymera on 2009-04-30
in firefox type this in the URL bar

```
 about:config 
```

search for ipv6 and it should come up with 1 or 2 results. Change it to enabled.

Search pipe and it will come up with lots of options, enable pipelining. 

These sped up my browsing a lot

---

### Post by Duskao on 2009-04-30
Not entirly sure or how to enable the option you are talking about, but I'm half way there :). As for a connectivity issue... well it's not an issue. I proved this to myself by using my wifes lap top at the same time, using the same router (she uses wireless, I'm hard line) and hers was working flawlessly... well as flawlessly as windows can :P. Like I said, it was working great before and almost instantly.

Skymera, would that solution work with Opera as well? Was having the same issue in Opera, but worse. Once it actually connected to the site it was blazing fast like opera normally is.

---

### Post by Duskao on 2009-04-30
Skymera, thanks! Seems to be working great again. Thanks a bunch!!!!

---

### Post by Neurosynapse on 2009-04-30
I was looking to speed up Firefox as well, but I can't find these options in my about:config O_o searched for both of them, and looked manually.

---

### Post by skymera on 2009-04-30
> **Duskao said:**
> Skymera, thanks! Seems to be working great again. Thanks a bunch!!!!

No problem :) Here to help 

@Neurosynapse: 
The exact names are:

network.dns.disableIPv6
network.http.pipelining
network.http.pipelining.ssl
network.http.proxy.pipelining

Enable all of them

---

