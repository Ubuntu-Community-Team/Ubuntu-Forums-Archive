---
title: "How do I 'quiet' the Networking keyring-daemon?"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by RobMBaker on 2007-04-23
Just a quick question, if anyone knows how to do this:-

I've started using the roaming option in Feisty, as it seems slightly more reliable than without; for my wireless network. Everything connects fine and well, but I am quite annoyed by the keyring-daemon asking me for a password EVERY time I boot, so it can load the WEP key for my network. Is there any way to disable this feature, and just have it connect without asking for a password? I know it's less secure that way, but I'm willing to store my WEP key without too much security; for the sake of not being asked for a password all the time!

Thanks in advance, for any help.

---

### Post by mariavon on 2007-04-23
Same thing....really annoying

---

### Post by rich.bradshaw on 2007-04-23
There is a thread on here somewhere where someone has released a new version of PAM which doesn't ask you for the password - was a bit dubious about installing it though, as was wondering if it will contiue to get updated using apt-get when newer versions are out. Looks like this will happen eventually anyway!

---

