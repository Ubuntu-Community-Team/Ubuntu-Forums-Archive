---
title: "Can ssh-agent be safely removed?  (basic 'buntu use, nothing special)"
date: 2017-10-06
forum: Networking &amp; Wireless
---

### Post by yoshii on 2017-10-06
I am wondering if the ssh-agent service can be removed on a typical 'buntu system.  
I have noticed that it is set to run by default and is always running unless I specifically kill it and/or disable the service.  
If I just remove it permanently, will there be any drawback?  Isn't it kind of a security risk to have it running all the time if I don't use it for anything?  

I am still able to connect to the internet and to do everything else as normal, so what's the point?  
I don't ever ssh into remote systems and I don't want anybody remote ssh-ing into my system, right? 

I can't fully comprehend all of this, but the following article lists a bunch of concerns about security hole problems with openssh:  
[https://www.ssh.com/ssh/openssh/](https://www.ssh.com/ssh/openssh/)

---

### Post by ajgreeny on 2017-10-06
Have you installed openssh-server?

Normally as far as I'm aware, only openssh-client is installed by default, and without the server version nothing can connect to your machine, or not in a straightforward way, at any rate, as it is not running the server service.

If you try to remove the openssh-client package it will also take several other packages with it, so make sure you know what you're doing if you choose that route.

---

### Post by yoshii on 2017-10-07
Hey thanks ajgreeny.  
I went ahead and removed all the ssh stuff on my system.  The agent, and openssh-client.  I never intend to turn my computer into a server.  It also removed snapd, but nothing else.  

I don't know what I need snap anything for, since it wasn't even available until just a few months ago.  But if I'm wrong, I guess I'll find out and then reinstall snapd by itself.  So far nothing has complained or crashed.  Nothing else got removed on my system which is Xubuntu.  

Overall, I'm trying to keep my system lean and without anyting extra.  Some of the leading security websites say that it's unhealthy and risky to have networking and internetworking services and programs installed by default if they are never used, because that's how hackers get in.  This was a humongous problem for MS Windows and is well understood these days by security folks who lived through that time.  It's still a problem with Windows.  

I really don't want to deal with that kind of vulnerability which is why I keep trying to choose minimal Linuxes.  Unfortunately, I keep learning about more and more stuff that I don't need or want being installed by default without any choice during the initial install.  I would try Arch or Manjaro but they look intimidating and there are technical hurdles.  I'm not quite at that level.  Yet, I am considering something like MX Linux to see if it's more minimal, but it's Debian and AntiX-derived.  

Anyway, at least it is possible to turn some stuff off and remove it.  I got fed up with some aspects of Windows 7 when I couldn't remove or turn them off without breaking the whole thing (scheduled tasks, in particular).  

I am running a digital audio workstation.  And every performance gain adds up in terms of preventing buffer underruns and being able to run more simultaneous audio effects or rendering to final audio faster.  So it's not actually trivial, whereas for an email/web browse/dvd watch user it might be irrelevant.  

But of course anybody can get hacked, and I'd rather not!

---

