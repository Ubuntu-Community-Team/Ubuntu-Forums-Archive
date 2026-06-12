---
title: "pulbic key error"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-05-01
how do i get this public key and how and where do i install it. note this is the error i get

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9F10E6AE9317790E

tks

---

### Post by coffeeaddict22 on 2009-05-01
Hi,
The package manager likes a key for any site you're downloading from.  To get this message, you've added something to your repositories... and there'll be a public key associated with it.  If you can remember what you were downloading when you first saw it, go to their site to find the key.  

If you open up the sources manager (System/Administration/Software Sources) for synaptic, there'll be a list of sites you've accepted as download sites under the "Ubuntu Software" and "Third Party Software" tabs, and a corresponding list under "Authentication" listing the keys you need for those sites.  If you can't remember what you added to your sources list, it'll be one of the sources in there.

---

### Post by sisco311 on 2009-05-01
To add the key, open a terminal and type:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 9F10E6AE9317790E
sudo apt-get update
```

[https://help.launchpad.net/Packaging/PPA#Adding a PPA's keys to your system]("https://help.launchpad.net/Packaging/PPA#Adding a PPA's keys to your system")

---

### Post by rburkartjo on 2009-05-01
sisco tks that is what i needed worked like charm

---

