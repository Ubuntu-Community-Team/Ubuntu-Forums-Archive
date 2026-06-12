---
title: "Access to routers web interface"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by xadloki on 2007-05-16
Is anyone having trouble getting into routers web interface ? I'm unable to open any routers web
interface in linux... I've tried Suse, Debian and currently I'm in Ubuntu... I have 3 routers and all are
connected through ethernet cable. My settings are perfectly setup and the connection is good,
the only thing I'm unable to do is open the web interface of any of my three routers 
(Linksys WRT54GL, D-Llink 604T and Comtrend CT-561). It launches the login popup but once
I type my login and password it just stays loading... 
Java, Flash etc are not needed for this so I don't have them installed, however I have tried it with
them installed with no result.  I am using firefox and it works fine in windows.

Any ideas on what is preventing the interface from loading ?
Linksys suggests to make sure there are no proxy settings on the browser which I have verified
and according to them it should work.

I did a little searching and seems someone had a similar problem in this thread 
[http://ubuntuforums.org/showthread.php?t=429750&highlight=web+interface](http://ubuntuforums.org/showthread.php?t=429750&highlight=web+interface)

He got the problem solved "[edit] Silly me!!! I just remembered I had changed the port it was listening to. "
I don't know what port he's refering to but it's possible that it might solve my problem...
Could anyone point me into the right direction on what he did?

---

### Post by Floppyjoe on 2007-05-16
To login he had to enter something like this into the browser window:
```
192.168.1.1:8080
```
He just needed to know the right port number. (ie 8080)

---

### Post by xadloki on 2007-05-16
cool thanks, i'll try that one after I find out what port it is. Usually I just type 192.168.1.1

---

### Post by xadloki on 2007-05-17
doesn't work... anyone have any other suggestions ? 
 Could it be my ethernet card that is a **** ? 
This is really annoying.

---

