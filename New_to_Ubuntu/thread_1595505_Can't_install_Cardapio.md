---
title: "Can't install Cardapio"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by andreylosev on 2010-10-13
I've read good things about the cardapio applet on OMG! Ubuntu, and I finally got down to installing maverick. However, I can't seem to install cardapio- here's what I get when I try to add the repository-

andrey@spider:~$  sudo add-apt-repository ppa:cardapio-team/unstable
[sudo] password for andrey: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 4DA8F2C6B86ED70787291C0BB2DFD25316B94077
gpg: requesting key 16B94077 from hkp server keyserver.ubuntu.com
gpg: key 16B94077: "Launchpad Cardápio unstable" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

---

### Post by andrewthomas on 2010-10-13
Where is the error?

What is the output of 
```
sudo apt-get update && sudo apt-get install cardapio
```

---

