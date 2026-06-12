---
title: "Can't reload Synaptic due to W.GPG error"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by nnjond on 2010-11-27
Hi,
I want to install KDE 4.5.3 but I cant reload Synaptic:

W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932

Can you help me please?

---

### Post by surfer on 2010-11-27
try this:
```
$ gpg --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
$ gpg --export --armor DB141E2302FDF932 | sudo apt-key add -
$ sudo apt-get update

```

---

### Post by nnjond on 2010-11-27
Great! Thanks

---

