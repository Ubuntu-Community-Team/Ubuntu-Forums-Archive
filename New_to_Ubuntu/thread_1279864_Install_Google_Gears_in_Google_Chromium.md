---
title: "Install Google Gears in Google Chromium"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-10-01
I am using Google Chromium in Ubuntu 9.04. Except for a few minor [hiccups]("http://ubuntuforums.org/showthread.php?t=1270830") it works pretty well. But, one thing that it lacks is [Google Gears]("http://gears.google.com/"). It works with Linux but only with Firefox natively. Is there any way to port it to Chromium?

---

### Post by abhiroopb on 2009-10-06
Bump!

---

### Post by tom.swartz07 on 2009-10-06
The short answer is, unfortunately no. Not yet. 

The last time I checked, Gears was not working with Chromium or the Dev-Builds of Chrome, BUT you could look and see for your current build. In GMail, go to settings/offline. If you could enable it, it should allow you. If you dont have the offline option, or you cannot enable it, then youre out of luck until the functionality is implemented.

The Dev-Builds update on a fairly regular basis, and they are constantly improving and adding things, so I am sure that Gears in Chrome is coming soon.

---

### Post by abhiroopb on 2009-10-06
Yea I already tried that. Thanks! It leads me to the google gears page and I'm told it doesn't work with Chromium. Shame :(

---

### Post by asoreyh on 2009-10-12
Same problem. It is a pity. I'm allowed to download only the gears.xpi file from gears home page, but it is not possible to install by any possible mean. We have to wait a bit more to get fully functionality on chromium, but it is a wonderful project.

---

### Post by Eestlane on 2009-10-25
Here's some info about it:
> **Q.** *I noticed that Gears source code has moved to the Chromium code repository. Why is that?*
**A.** With Gears as a plug-in to Chromium we're carrying two copies of sqlite and two copies of V8. That's silly. We're **integrating the code** so Gears can run great in Chromium. We plan to continue to build Gears for other browsers out of the same code base.

[http://dev.chromium.org/developers/faq](http://dev.chromium.org/developers/faq)

However, it's not going to be very soon for Linux. You can track it here:
[http://code.google.com/p/chromium/issues/detail?id=17443](http://code.google.com/p/chromium/issues/detail?id=17443)

---

### Post by asoreyh on 2009-10-25
Perhaps Karmic will solve this problem. According comment 3 in the thread you mentioned,

[http://code.google.com/p/chromium/issues/detail?id=17443#c3]("http://code.google.com/p/chromium/issues/detail?id=17443#c3")

gears will be available in Karmic: 
> 
Comment 3 by [email]fta@sofaraway.org[/email], Jul 22, 2009
FYI, gears is in Ubuntu Karmic (future 9.10)
[http://packages.ubuntu.com/search?keywords=gears&searchon=names&exact=1&suite=all&section=all]("http://packages.ubuntu.com/search?keywords=gears&searchon=names&exact=1&suite=all&section=all")
[http://packages.ubuntu.com/karmic/gears]("http://packages.ubuntu.com/karmic/gears")


---

### Post by renkinjutsu on 2009-10-25
doesn't Google Gears just make browsers more compatible with a lot of HTML5 features? Chromium is already an HTML5 capable browser, why use gears?

---

### Post by asoreyh on 2009-10-25
I started looking for gears for chromium when I moved from Firefox to Chromium, just because Offline gmail is disabled on chromium (Offline Gmail settings say you need to download and install gears).

My chromium version: 4.0.224.4 (Ubuntu build 30004) on Jaunty.

---

### Post by abhiroopb on 2009-10-25
> **renkinjutsu said:**
> doesn't Google Gears just make browsers more compatible with a lot of HTML5 features? Chromium is already an HTML5 capable browser, why use gears?

The main benefit of gears is that you can use most of google webapps offline (i.e. view e-mails offline).

---

