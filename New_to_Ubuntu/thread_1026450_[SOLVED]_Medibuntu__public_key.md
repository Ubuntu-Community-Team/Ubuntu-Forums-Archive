---
title: "[SOLVED] Medibuntu  public key?"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by jorge ortega on 2008-12-31
I installed medibuntu repositories to Synaptic and the packages are there and I can install them no problem but when i run the update manager this is what i get:
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

What key is that? should i do something about it or i shouldn't bother?

I'm on Hardy Heron

---

### Post by Michael.Godawski on 2008-12-31
hi, 

usually the process of adding the medibuntu repositories is as follows:

adding the sources:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```adding the key:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by jorge ortega on 2008-12-31
Thanks Godawsky, that solved the problem whatever the problem was.

---

