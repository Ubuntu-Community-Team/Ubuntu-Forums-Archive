---
title: "How do I fix public key not available"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by trooperchix on 2009-05-21
```

GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0B47F0A6B88A1AA8


```

I have no clue.

---

### Post by tomcheng76 on 2009-05-21
try **sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0B47F0A6B88A1AA8** ?
If not work, see [here]("https://help.launchpad.net/Packaging/PPA")

---

### Post by binbash on 2009-05-21
[http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html](http://www.ubuntu-inside.me/2009/02/howto-fix-signaturekeyserver-problems.html)

---

