---
title: "software manager"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by nick_goodfate on 2010-06-17
hi! when i run apt-get update i get this error :
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9A681FDFB80E4D96

any ideas ? i gues i have to import a public key ... ?:confused:

---

### Post by wojox on 2010-06-17
Run these two commands

```

gpg --keyserver pgpkeys.mit.edu --recv-key  9A681FDFB80E4D96 
gpg -a --export 9A681FDFB80E4D96 | sudo apt-key add -

```

---

### Post by cnkbrown on 2011-02-07
> **wojox said:**
> Run these two commands

```

gpg --keyserver pgpkeys.mit.edu --recv-key  9A681FDFB80E4D96 
gpg -a --export 9A681FDFB80E4D96 | sudo apt-key add -

```

I get this error;

```
gpg: requesting key B80E4D96 from hkp server pgpkeys.mit.edu
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

```

could my corporate firewall be blocking this?

---

### Post by oldos2er on 2011-02-07
Can you go to [http://pgpkeys.mit.edu/](http://pgpkeys.mit.edu/) in your browser? The site is really slow for me.

---

