---
title: "Validating and using a Openpgp key in Yahoo mail"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by anewguy on 2011-09-03
I received the confirmation email for my launchpad registration of my openpgp key, but can't read it.  The link it says to follow for instructions doesn't list Yahoo free web based email.  I have no other email.  Is there a way to do this?

Thanks in advance!

Dave ;)

---

### Post by haqking on 2011-09-03
> **anewguy said:**
> I received the confirmation email for my launchpad registration of my openpgp key, but can't read it.  The link it says to follow for instructions doesn't list Yahoo free web based email.  I have no other email.  Is there a way to do this?

Thanks in advance!

Dave ;)

Cant you use a client such as Evolution to access your mail ?

---

### Post by anewguy on 2011-09-03
Tried it before using a cheat to get access to my Yahoo mail - the result ends up being a confusing mess, needing to sync all the time and try to keep things straight.

Thanks for the reply!

Dave ;)

---

### Post by anewguy on 2011-09-03
Found there was a help for gmail - it ended up working for Yahoo mail as well.  It installed a package for pgp, then you run it in the terminal - it takes a txt file containing the encoded portion of the mail and writes out a file of the unencoded result.  This allowed me to complete the registration.

just in case someone else needs this and they also use Yahoo web based email.

Dave ;)

---

### Post by haqking on 2011-09-03
> **anewguy said:**
> Found there was a help for gmail - it ended up working for Yahoo mail as well.  It installed a package for pgp, then you run it in the terminal - it takes a txt file containing the encoded portion of the mail and writes out a file of the unencoded result.  This allowed me to complete the registration.

just in case someone else needs this and they also use Yahoo web based email.

Dave ;)

ahh cool. Glad you got it sorted.

It appears there is a few issues with the PGP thing for launchpad, there is a bug reported on it as well it being convoluted.

---

