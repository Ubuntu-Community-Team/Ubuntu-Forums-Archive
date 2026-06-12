---
title: "Installed Single Boot Ubuntu 10.10 - Very Slow Internet Surfing"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by Flood-X on 2011-01-18
Hello everyone,

After trying out Ubuntu through the Wubi Install, I decided to reinstall Ubuntu again (10.10) and reformat my hard drive since I wanted to throw away Windows.

Anyway, so I did a clean install of Ubuntu 10.10 (the latest stable release) and I noticed that when I'm browsing the web, it takes forever for a web page to load. I keep getting "waiting for www.google.com" for example, when I'm trying to go to google.com in Firefox.

I did a quick search in google and on the forums, and there is a lot of talk regarding disabling IPv6 and changing DNS settings. All of them were regarding older releases of Ubuntu where the default for IPv6 in Network Manager was to have it on. With 10.10 it is defaulted to off under Network Connections for "auto eth0". (I'm not using wireless. This is a desktop.)

This problem didn't exist when I was using Windows XP.

I tried disabling the IPv6 setting in Firefox, but it didn't solve the problem. I also tried setting up OpenDNS, but that also didn't really solve the problem.

The problem is most obvious when I try opening [www.google.com](www.google.com)
It takes 20-30 seconds, whereas when I was using Windows XP, it would take 1-2 seconds.

Any suggestions?

---

### Post by Flood-X on 2011-01-18
Actually, it took also 30 seconds to post the above.

I'm wicked sad, because I really don't want to reinstall Windows XP. I hate Microsoft and their Empire of Monopoly.

---

### Post by HereInOz on 2011-01-18
No help at all but I am having the same issue with two Ubuntu machines at one location,  I find that often if you click the link again, it actually works that time.

One of the machines is a laptop, and it works fine everywhere else but on this particular network.  I, too, would love to find a solution.  I have also tried Chrome and Opera with no success, and also have tried OpenDNS but again, no joy.

One of the installs is 9.08 and the other is 10.04.  It is a mystery to me.

Hope someone comes up with a solution.

---

### Post by ExileAmongYou on 2011-01-18
A couple things you could do:

Try a different browser (Chromium maybe?)

Check that your connection isn't running through a proxy or a vpn

```
ping www.google.com
```
and see how long it takes.

Sorry that I don't have any specific suggestions.

---

### Post by Flood-X on 2011-01-18
I'm sorry, I just pulled out my old laptop with Windows XP installed. It seems that this isn't an Ubuntu problem but rather either an ISP or router problem.

Thank you everyone for your replies.

---

