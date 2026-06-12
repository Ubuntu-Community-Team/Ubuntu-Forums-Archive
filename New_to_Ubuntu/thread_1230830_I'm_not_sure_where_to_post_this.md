---
title: "I'm not sure where to post this"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by LxxRyuzaki on 2009-08-03
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 99D6B21CC6598A30

How do I fix this?

---

### Post by philcamlin on 2009-08-03
are you on a dell mini?
and tun 
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 99D6B21CC6598A30

---

### Post by wojox on 2009-08-03
Run this:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 99D6B21CC6598A30
```

---

### Post by LxxRyuzaki on 2009-08-03
what you said might work, but I'm letting you know that I have a Acer Aspire One, that's using Ubuntu 9.04

---

### Post by wojox on 2009-08-03
It'll work and if it doesn't it's phil's fault.

---

