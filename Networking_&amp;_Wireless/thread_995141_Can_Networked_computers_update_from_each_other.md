---
title: "Can Networked computers update from each other"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by sad1sm0 on 2008-11-27
Hi All, thanks in advance for any help.  I've been using Ubuntu for probably 4 months now.  I usually can find whatever I need help with already posted in the forums so I haven't posted anything yet.  Anyway, I have a couple of questions that all kind of tie together.

First, I just installed intrepid on a Dell Latitude C400 with a linksys wpc54g wireless card.  Everything works for the most part except occasionally I lose networking and have to restart networking.  not a huge deal except that I am the only user with sudo privileges so I need to restart it each time.  Otherwise, whoever might be using the computer needs to restart it.  So I ask, (A) - has anyone found a solution to this problem (I've read a few posts with no solutions really) or (B) - Is there some way for me to authorize other users to restart networking without there account being sudo.  Could add a launcher to the desktop and just authorize them to do that one sudo action?

Second: I recently got a notice that my bandwidth usage is exceptionally high and that my isp is going to continue to monitor my usage.  I'm a web developer, and I had a client send me a ton of super large images for a photo gallery via email plus I ended up needing to download ubuntu 5-6 times in 1 month (huge issues).  I think that this is what set it off, but I need to cut down at least for a bit.  So I'm wondering if there is some way to update the laptop with packages that I have already downloaded to the main box in my house.  I have all most of the same stuff installed on that one and a few extras.  I know I can copy my package cache and do something with dpkg to update from that, but how can i use |grep to find only the packages I need for the other computer?  Or is there some way to tell it to search from my computer for upgrades first?

Thanks again to anyone who happens to be able to help

---

### Post by steeleyuk on 2008-11-27
For the second question, the application you're looking for is apt-zeroconf. This [page]("http://michael.susens-schurter.com/blog/2006/12/12/apt-zeroconf/") has decent instructions on using it.

---

### Post by HavocXphere on 2008-11-27
Perhaps something like this?
[http://news.softpedia.com/news/Create-a-LAN-Repository-with-Apt-Cacher-45978.shtml](http://news.softpedia.com/news/Create-a-LAN-Repository-with-Apt-Cacher-45978.shtml)

---

