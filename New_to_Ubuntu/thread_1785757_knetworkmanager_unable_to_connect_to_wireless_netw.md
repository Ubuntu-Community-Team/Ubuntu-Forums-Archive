---
title: "knetworkmanager unable to connect to wireless networks"
date: 2011-06-18
forum: New to Ubuntu
---

### Post by wishingstar on 2011-06-18
Hello everyone.

After being disappointed with unity, I decided to make the move to KDE. Ever since I made the move, I am facing a weird problem with knetworkmanager. I tried to do a search, but I can't seem to find an answer to my specific issue:

Knetworkmanager can connect to my (WEP-protected) home Wifi just fine, the connection is pretty much stable without many issues, however, every time I try to connect to another network, it keeps asking for the password (although I have entered it right) and refuses to connect, this happened in 2 of my friends houses and at work, I can't seem to be able to connect to ANY network other than my home's wirelessly (even though the networks i try to connect to are also WEP-protected). Wired DSL works fine though, which is another weird thing.

I appreciate any help you can give,
WishingStar

---

### Post by Laforge129 on 2011-06-18
> **wishingstar said:**
> Hello everyone.

After being disappointed with unity, I decided to make the move to KDE. Ever since I made the move, I am facing a weird problem with knetworkmanager. I tried to do a search, but I can't seem to find an answer to my specific issue:

Knetworkmanager can connect to my (WEP-protected) home Wifi just fine, the connection is pretty much stable without many issues, however, every time I try to connect to another network, it keeps asking for the password (although I have entered it right) and refuses to connect, this happened in 2 of my friends houses and at work, I can't seem to be able to connect to ANY network other than my home's wirelessly (even though the networks i try to connect to are also WEP-protected). Wired DSL works fine though, which is another weird thing.

I appreciate any help you can give,
WishingStar

It looks to be a bug in KDE, Please see:

[http://bugs.kde.org/228298](http://bugs.kde.org/228298)

Only way to change that is to have all the routers you are trying to connect to use the passphrases and not ASCII text!

---

### Post by wishingstar on 2011-06-18
Thanks for responding Laforge129, so apparently (from the link you posted) this bug will be fixed in the next KDE release? or have i misunderstood that?

Also, for now, as a general rule: if the network does not accept a passphrase, i change to ascii and re-enter the same network code?

Thanks for the help

---

### Post by wishingstar on 2011-07-21
This has be recently solved by using ascii instead of passphrase, would think kde should be able to detect this on its own!

---

