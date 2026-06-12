---
title: "NO_PUBKEY 71346C8340130828 - Is this important?"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by Irish1 on 2009-04-20
NO_PUBKEY 71346C8340130828 - Is this important? And if so what does it mean and how do I remedy it?

Thanks again everyone.

---

### Post by sisco311 on 2009-04-20
Yes, it's important: [https://help.launchpad.net/Packaging/PPA#Installing software from a PPA]("https://help.launchpad.net/Packaging/PPA#Installing software from a PPA")

> Your PPA's key

Launchpad generates a unique key for each PPA and uses it to sign any packages built in that PPA. 

This means that people downloading/installing packages from your PPA can verify their source.

to add the key:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 71346C8340130828
```

---

### Post by unutbu on 2009-04-20
Repositories use GPG keys to sign packages. By downloading the public key associated with a repository, your system can verify that it is getting authentic packages from that repository. 

To download the public key 71346C8340130828, open a terminal (Applications>Accessories>Terminal) and type:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 71346C8340130828
```

---

### Post by sadicote on 2009-04-20
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 71346C8340130828
gpg --export --armor 71346C8340130828 | sudo apt-key add -

then update once more.

---

### Post by Irish1 on 2009-04-20
The advice found in this forum worked again, cheers guys, I don't know what I would do with out all of your help.

---

### Post by steve101101 on 2009-04-20
> **Irish1 said:**
> The advice found in this forum worked again, cheers guys, I don't know what I would do with out all of your help.

you will quickly find out that this forum is extremely useful.

---

