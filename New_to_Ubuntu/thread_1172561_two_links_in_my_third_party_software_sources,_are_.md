---
title: "two links in my third party software sources, are they supposed to be there?"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by djmh on 2009-05-28
these are in my third party software sources, and are unchecked....can i remove them?

one is
archive.canocal/ubuntu jaunty(source code)
the other is
archive.canocal.com/ubuntu jaunty (partner)

can those be removed, or are they neccassary for something?

---

### Post by Sealbhach on 2009-05-28
I would tick them and keep them if I were you. These allow access to third party software:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

> The "Third-Party Software" tab is where you will be able to add the Canonical Partner Repositories. You will see two Canonical Partner repositories listed - one for applications and another for source code (src). The partner repositories offer access to proprietary and closed-source software and are not enabled by default.

.

---

### Post by djmh on 2009-05-28
ah i see, thanks man
but the reason i ask is beacause when i hit reload i get this error

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5

---

### Post by Sealbhach on 2009-05-28
OK, run this command in a terminal:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5A9BF3BB4E5E17B5
```

This will get you the key.

.

---

### Post by djmh on 2009-05-28
awesome man, thanks !
but just kinda for reference...how did you get that?
i mean if its not too much trouble, i like to learn what it is im doing not just copy paste and be done....

---

