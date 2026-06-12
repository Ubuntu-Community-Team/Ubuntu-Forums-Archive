---
title: "Automatically Pause Downloads"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by asforme on 2008-01-13
I have an Ubuntu 7.10 Server running hellanzb and torrentflux, though I hardly ever use torrentflux, heallanzb is downloading constantly maxing out my connection.  I want some way to automatically pause the heallanzb downloads for 30 seconds every time my server detects internet activity.

I have tried using QOS on my router and it just slowed down my entire connection.  I do not want to use QOS on my server because that requires either making my server into a firewall not to mention that QOS tends to increase latency in games.

My server is running squid, but I only want to use that for http.  Trying to play games through a proxy doesn't sound like a good idea.

Instead I want my server to simply see that I am doing something on the internet (gaming, web browsing, skype, whatever) and pause my downloads for 30 seconds, then check and see if the internet is not being used.

It would be even better if I could customize it to specify just how much activity is needed so that my downloads don't pause every time pidgin pings AIMs server, but just getting something to work at all would be nice.

Thanks for your help.

---

### Post by enuf on 2008-01-17
Search forum for wondershaper. 
Helped me out with maxed out conections...
[http://ubuntuforums.org/showthread.php?t=25911]("http://ubuntuforums.org/showthread.php?t=25911")

---

