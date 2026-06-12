---
title: "What does this terminal output mean?"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by AndyP79 on 2011-01-25
Hi Folks,
 I was adding a PPA via the Terminal this morning, and I got this out put

sudo add-apt-repository ppa:fredp/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv E2BF776503094A66E3E94745BF60DE29B3246C76
gpg: requesting key B3246C76 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: No route to host
gpgkeys: HTTP fetch error 7: couldn't connect: No route to host
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


I have had this and other ones telling me that the pubkeys for maverick are not good either. Anyway to fix missing pubkeys and explain what this above one is saying?
Thanks

---

### Post by mtron on 2011-01-25
> keyserver.ubuntu.com: No route to host

You were either not connected to the Internet, or the ubuntu keyserver was not avaiable. 

So check that your Internet works and try it again. The keyserver is up and running (just checked it now).

---

### Post by philinux on 2011-01-25
If you search on say google for this 
"keyserver.ubuntu.com: No route to host"

You will find a few solutions. It seems like a network problem.

---

### Post by AndyP79 on 2011-01-25
Cool thanks guys. Sounds like it is just a temporary thing then due to the network. We got a funny line sometimes at work cause of the IT guys playing around. Though, we do get 300MbSec!! I'll run the update again.

---

