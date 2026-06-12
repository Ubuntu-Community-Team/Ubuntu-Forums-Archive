---
title: "Hiding the OS with proxy or something else???"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by ssc351 on 2007-09-01
Hey everyone, 

So i started messing around with proxies a little bit to beef up the security on my computer.  One of the things I noticed is that when I am running the proxy through firefox with tor and prioxy if I go to google.com, it brings me to the dutch site...which isn't that big of a deal because you can just click on the english site, and I guess it is a known bug from other searches i have done.  Anyway, I also downloaded user agent switcher for firefox which I guess is supposed hide your OS and browser but when I do a search in google, I notice that part of the web address included "ubuntu"  So is my OS really being hidden?  And is there a way to hide it?

---

### Post by BrendanM on 2007-09-01
The reason you're seeing the Dutch google is likely because the proxy you're using is in the Netherlands. It's not really a "bug" it's just google trying to direct you to the appropriate page based on what it thinks your IP address is.

 As for the other issue, installing user agent switcher alone won't change your user agent. You need to go to find a list of user agents (try here: [http://techpatterns.com/forums/about304.html](http://techpatterns.com/forums/about304.html)) import them into user agent switcher, and then actually change it to one of the new ones.

Also, unless you have a good reason, I would suggest against changing your user agent. We want website administrators to know that Linux users and Firefox users are out there. That way, maybe they won't code sites just for IE on WIndows. If we all pretend to be running IE, they won't even know there's an issue.

---

