---
title: "Downloading package error !"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by sharbeloun on 2008-12-16
Hi all;

when i try to reload the packages with "synaptic package manager"
if starts downloading and then it stops suddenly and i get this message !

> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783



What to do ?

---

### Post by Michael.Godawski on 2008-12-16
hi, 
let's first try this. Open the terminal and run:
```
 wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
```

if this not helps have a look at this thread
[http://ubuntuforums.org/showthread.php?t=983132](http://ubuntuforums.org/showthread.php?t=983132)
Perhaps some of the solutions presented there will solve it for you.

---

