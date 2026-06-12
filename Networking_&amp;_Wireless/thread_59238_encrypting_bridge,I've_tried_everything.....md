---
title: "encrypting bridge,I've tried everything...."
date: 2005-08-23
forum: Networking &amp; Wireless
---

### Post by odin on 2005-08-23
I read in [http://www.arnor.net/encryptingbridge/](http://www.arnor.net/encryptingbridge/) (I was redirected there from bridge.sourceforge.net/devel.html) that it is possible to encrypt data flowing through a bridge applying a patch to kernel 2.4.19-pre8 and then installing a package.

I've tried everything.I compiled the pre-patched kernel I made the simlink they say there but still when type make for compiling the package then i get some errors and I cant go on.I even tried installing red hat 7.2 cause I dont know why I got the feeling that packet was meant for that distribution and in a old version.

I was just wondering if anyone have tried that in ubuntu or any other distro and could help with it.Even any tip about installing a package from source so maybe I can see my mistake.The package doesnt have the configure file so maybe there's something I need in my system.

with tiny hope,thank's in advance.

(Dont worry I'll not kill myself,I'm closed to and I'll get fired but I'll not do it)   ;-)

---

### Post by odin on 2005-08-24
ok I can see that was a very wide question so I'll ask a smallest question to see if someone can help me to see the light.


From [www.arnor.net/encryptingbridge:](www.arnor.net/encryptingbridge:)


"To compile this application, you will need to make /usr/include/linux a symlink to your patched kernel tree include/linux to pick up the #defines for the new IOCTLS. (yeah, I know, it should have a private header file... sorry.)"


what is the IOCTLS?
what does exactly mean saying "....to pick up #defines for the new IOCTLS."?
and finally,how would you do this symlink,just with "ln -s" or there's anything I'm missing?


My knowledge in programming at this level are closed to 0 and everytime I try to compile I get a bunch of errors like " BRCTL_GET_PROTOCOL_FILTER_MODE undeclared (first use in this function)" so I guess it has something to do with the IOCTLS or even I have to change something in the code.


thank's in advance.

---

