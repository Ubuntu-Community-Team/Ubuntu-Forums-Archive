---
title: "key error.."
date: 2010-04-28
forum: New to Ubuntu
---

### Post by joenewtzie on 2010-04-28
getting this key error:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


What do I put into the terminal to fix this?

---

### Post by todak on 2010-04-28
```
sudo apt-get install medibuntu-keyring
```

---

### Post by wojox on 2010-04-28
Run these in the terminal

```
gpg --keyserver subkeys.pgp.net --recv 2EBC26B60C5A2783
```


```
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -
```

---

### Post by joenewtzie on 2010-04-28
> **wojox said:**
> Run these in the terminal

```
gpg --keyserver subkeys.pgp.net --recv 2EBC26B60C5A2783
```


```
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -
```

That did it! I saved those commands because it seems I just copy and paste that bundle of numbers/letters (2EBC26...) and that works everytime!

---

