---
title: "Removing proxy settings in Jaunty jackalope"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by prasaanth on 2009-10-07
Hello all,

I am a newbie to linux and have been using the ubuntu 9.04 in my laptop for quite some time. In my college, I connect to the internet via a proxy server. I was able to remove the proxy for my home connection, however my sudo apt-get or updating my software resources show me that "couldn't resolve proxy.ssn.net" message every time I try to download something or update any softwares. I had actually deleted /etc/apt/apt.conf . Please elaborate on what should I do to resolve this ??

Thanks in advance,

Prando :)

~If you think of MS-DOS as mono, and Windows as stereo, then Linux is Dolby Pro-Logic Surround Sound with Bass Boost and all the music is free.~

---

### Post by tomBorgia on 2009-10-08
Hi.

Open up synaptic > settings > network...

You can change the proxy settings there... I *think they'll carry over to apt (as synaptic is pretty much a gui for apt...)

---

### Post by jolarson on 2009-10-08
I am actually having a similar problem, and changing the proxy in System - Preferences - Network proxy does not resolve.  even if there is no proxy set apt-get still tries to connect to the former proxy.  I have also checked in Synaptic and there is no proxy there either.  I have looked through previous posts, but to no success.  Any help would be appreciated.

---

