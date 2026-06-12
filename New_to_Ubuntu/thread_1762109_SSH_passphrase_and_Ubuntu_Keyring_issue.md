---
title: "SSH passphrase and Ubuntu Keyring issue"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by beeltejuice on 2011-05-18
I am running a new install of ubuntu 10.10 and have a ssh key with a passphrase.  Whenever I first attempt to use that key during a session, I get prompted to enter the passphrase.

With my previous install (can't remember if 10.10 or 10.04) I only had to enter the passphrase once and then I was prompted to ask if I should unlock the keyring upon log-in.  I checked yes and never had to enter my passphrase again.

How do I go back to this?  Does this ring any bells with anyone?  And for the record, my ssh passphrase is different than my log in password, and no I don't want to make them the same.

I'm stumped.  Thanks in advance!

---

### Post by wojox on 2011-05-18
I think your looking for

```
gksudo seahorse-preferences
```

---

