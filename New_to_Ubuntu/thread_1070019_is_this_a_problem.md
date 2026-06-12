---
title: "is this a problem"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by kapi on 2009-02-14
received this when updating 

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

wondered if it was a problem?

Thanks

---

### Post by kestrel1 on 2009-02-14
No shouldn't be a problem.
There should be a way around it though. Once I remember what it is I will post it.

---

### Post by llamabr on 2009-02-14
Not really, but a better way to add the mediabuntu to your sources list is by getting the key.  Do a:

wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

---

### Post by yeats on 2009-02-14
I'm assuming you're following the instructions on this page (?):

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

It says:

> Then, add the GPG Key:
```

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

You may be asked to accept this package even though it cannot be authenticated. This is normal; typing "Yes" means you trust Medibuntu. 

Follow those instructions and you should be good.

---

