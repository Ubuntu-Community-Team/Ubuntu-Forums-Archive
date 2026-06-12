---
title: "Indicator applet/gwibber service"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by vivek40 on 2010-05-04
Hi .. I noticed that indicator applet and the gwibber service suddenly surges upto use 100% of CPU . It remains like that for close to a minute before going down. I am using Lucid.. it is a fresh clean install.. and could someone also educate me on "desktop couch service". I see two instances of it running in my system monitor. And then there is Ubuntu one sync daemon & the "Ubuntu one login" which are together using close to 26MB of RAM. Why is it so when I am not even using Ubuntu one. 

I know this post has been poorly framed... but then please help !

---

### Post by Jon Monreal on 2010-05-04
If you don't plan on using Ubuntu One (or the music store) at all, you can
```
sudo apt-get remove &#8211;purge ubuntuone-client
```
to get rid of Ubuntu One.

For more information on desktopcouch-service, please see [here]("http://www.freedesktop.org/wiki/Specifications/desktopcouch/Documentation/How_Desktopcouch_Works") (short version: you need it).

With Gwibber, you may be experiencing a bug such as [this one]("https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/451360"). As suggested there, you could use [cpulimit]("http://cpulimit.sourceforge.net/") to limit Gwibber's CPU usage. If you need help doing this, please feel free to ask.

---

### Post by vivek40 on 2010-05-04
Thanks Jon! But I removed gwibber and surprisingly now "Ubuntu one sync daemon" & the "Ubuntu one login" are fixed. I mean now they are not using that 26MB RAM when I was not even using them. I cant figure out how can both gwibber and Ubuntu one be linked in any way.

Secondly , the indicator applet still surges upto use 100% CPU for a few seconds. There are a few instances when both "top" and "system monitor" shows it as using 200%CPU for a few seconds.Can someone please help me with this?

---

### Post by Jon Monreal on 2010-05-04
I see that you already posted in the comments for a bug in indicator-applet.

Perhaps you could try using cpulimit to limit its usage, in the same way you might use it with Gwibber.

Is the high CPU usage disruptive? Perhaps you should file a new bug if you think it's abnormal.

---

