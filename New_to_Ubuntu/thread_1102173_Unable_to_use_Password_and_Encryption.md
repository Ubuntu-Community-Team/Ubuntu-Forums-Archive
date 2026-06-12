---
title: "Unable to use Password and Encryption"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by leeds on 2009-03-21
I am trying to generate a key using the default Password and Encryption software, however I am unable to generate keys. During the key generation phase after I enter my pass phrase I get the following error "Couldn't generate PGP key - General Error" - am I missing a software or application on my system?

---

### Post by Bachstelze on 2009-03-21
Try from a terminal:

```
gpg --gen-key
```

Also, if you want a GUI program and don't mind installing a lot of additional libraries, you could give Kgpg a try. It's much better than Ubuntu's default program IMHO.

---

