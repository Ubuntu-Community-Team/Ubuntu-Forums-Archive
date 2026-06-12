---
title: "public key error"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-01-22
i am getting this error how do i fix

W: GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF
tks

---

### Post by sisco311 on 2010-01-22
Add the public key to the list of trusted keys:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 46D7E7CF
```

---

### Post by rburkartjo on 2010-01-22
tks sisco you helped me before with a similar problem. now i know just to use the last 8 digits of the key with sudo apt-etc

---

