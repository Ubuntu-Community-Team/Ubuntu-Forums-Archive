---
title: "Error Message in Synaptic"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by old_dope on 2009-03-06
When i enter Synaptic i get the following error message. Could someone tell me what is happening here and how i may resolve this please. Thanks in advance.

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by sgosnell on 2009-03-06
It's telling you that it doesn't have a key to verify the repository.  You can ignore it if you want, it won't prevent getting the files.  Or you can get it with ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg
```

---

### Post by plucky on 2009-03-06
> **sgosnell said:**
> It's telling you that it doesn't have a key to verify the repository.  You can ignore it if you want, it won't prevent getting the files.  Or you can get it with ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg
```

That command will only get you the key,you still have to add it to software sources.

Try to copy and paste to a terminal  ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```


Good Luck

---

### Post by old_dope on 2009-03-06
Big thanks folks!

---

