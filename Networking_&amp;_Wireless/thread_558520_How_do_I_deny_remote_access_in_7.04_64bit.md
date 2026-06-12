---
title: "How do I deny remote access in 7.04 64bit?"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by Udibuntu on 2007-09-24
Hey Guys,

How do I deny remote access to my PC? Is it done by default?

The only person who knows my location on the web is an ISP rep who supported my login once. 

Am I paranoid to ask? :)

Yours,

Udi

---

### Post by Soarer on 2007-09-24
System >> Preferences >> Remote Desktop (at least on Gutsy)

Mine is turned off by default.

Yes, you should be paranoid :)

---

### Post by denver on 2007-09-24
By default there are no open ports in Ubuntu. There are no services running on it that listen for incoming connections. So don't worry about anybody connecting to your PC.

On the other hand, if you have installed apache, ssh or any other service that listens for client connections, and you really don't want anyone else to use them but you ( for one reason or another ) then you could block all incoming connections via iptables.

```
iptables -A INPUT -p tcp -j DROP
```

However, this measure is extreme and completely unnecessary( in my opinion ). If you really did install ssh for remote access then you could just lock it down a little ( ex: use key authentication, disable password authentication, etc ). One more thing to keep in mind is that your PC will be vulnerable because of a running service, only if that service has a bug that can be exploited in some way or another.

But again, if you have not installed any services on your PC, then you have nothing to worry about.

---

### Post by Udibuntu on 2007-09-24
Soarer, Denver - Thanks a bunch.

No such apps are running and option for remote DT is unchecked.

I'll keep investigating in security forums to make myself more acquainted with security on Ubuntu.

BTW, I just remembered the rep suggested I define a root password instead of using sudo  - being starry eyed I did that, and now wonder if I need the Day After Pill or something... :(

What do you think?

Udi

---

### Post by Udibuntu on 2007-09-24
btw, started using Firestarter (GUI for iptables suggested by Denver).

---

