---
title: "medibuntu key failure"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by dndrich on 2009-11-15
Ubuntupals:

I installed medibuntu to my software sources via the usual way by terminal. For some reason I keep getting this error message when updating software sources:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


Now, all the software loads just fine, and I am able to get all the updates and extras. I just wonder what the problem is here? I am running karmic 64 bit.

---

### Post by ranch hand on 2009-11-15
What happens if you run this;
```

wget --quiet http://packages.medibuntu.org/medibuntu-key.gpg -O - | sudo apt-key add -

```

---

### Post by dndrich on 2009-11-15
That did it. I must have missed doing that. Thanks!

---

### Post by ranch hand on 2009-11-15
Oh geeze that is great.  May not make you feel real bright (I am good at these types of things) but it could have been a problem.

---

