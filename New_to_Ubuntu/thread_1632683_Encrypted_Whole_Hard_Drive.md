---
title: "Encrypted Whole Hard Drive"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by yeh on 2010-11-28
when installing, I checked the option to encrypt the whole hard drive. Now, nothing has gone wrong so far, but there was a message which I carelessly X'ed out that said it would tell me the encryption key to my hard drive which I should keep in a safe place. Just in case my regular password doesn't work to decrypt the drive.

Like I said, I x'ed it out. And it doesn't seem to be popping up again, ever. Isn't there a terminal command I can use to find the encryption key to my hard drive?

Thx.

---

### Post by Paqman on 2010-11-28
I believe it's:
```
ecryptfs-unwrap-passphrase ~/.ecryptfs/wrapped-passphrase
```

Btw, unless you used the Alternate CD and set up full drive encryption specifically, it's only your home folder and swap that's encrypted, not the whole drive.

---

