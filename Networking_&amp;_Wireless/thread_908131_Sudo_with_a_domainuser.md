---
title: "Sudo with a domainuser?"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by wesleydb on 2008-09-02
Hi,

I'm trying to get a computer on our domain.  The problem is in order to do so the first thing i have to do is:

sudo apt-get update

which results in:

err [http://security](http://security) etc...
could not connect to security ubuntu.com:80 (91.189.88.37), connection timed out

well i am connected to the network (i can surf the net using firefox (after authentication)).

I asume i have to use a domainaccount to get past the proxy server.

Something like: sudo -u domain\user apt-get update

But then in a way that this would work :p.

Any idea's?

Grtz

---

