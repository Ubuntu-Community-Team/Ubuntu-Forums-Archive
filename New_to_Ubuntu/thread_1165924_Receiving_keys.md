---
title: "Receiving keys"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by bacardiandwatermelon on 2009-05-21
Hi guys, I'm just trying to get my head around this whole key thing but I was wondering what the difference was between..

```
gpg --keyserver subkeys.pgp.net --recv-keys <key>
gpg --armor --export <key> | sudo apt-key add -
```and

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <key id>
```Am I guessing wrong that ultimately they both do the same thing? I have always used the latter, but is using the first way better somehow?

---

### Post by bacardiandwatermelon on 2009-06-05
bump :-)

---

### Post by Tibuda on 2009-06-05
You are fine using it.

As I see, the second "installs" the key directly to the apt keyring, but the first "installs" it on your user keyring, and then export it to the apt keyring.

---

