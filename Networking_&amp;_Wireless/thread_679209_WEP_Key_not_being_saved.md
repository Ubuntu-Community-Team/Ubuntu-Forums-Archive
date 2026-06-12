---
title: "WEP Key not being saved?"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by zensuckit on 2008-01-26
A little bit after new year's, my girlfriend's Inspiron 700m with Gutsy stopped remembering my WEP key.  Typically, she enters her keyring password and it automatically connects to my network.  I'm assuming there was an update that screwed it up, but have not seen a subsequent update to fix it.  I haven't been able to find anything via search.  Is this a known issue, or am I on my own?

---

### Post by jackocleebrown on 2008-01-27
Are you connecting using network manager? Check that the password is being entered in the keyring (system-administration-keyringmanager). there are also some settings here for allowing applications to access info in particular key rings. Might be worth trying deleting the key that has the passcode that does not work and then reconnecting - this will add it again as a new entry in the keyring.

Jack.

---

