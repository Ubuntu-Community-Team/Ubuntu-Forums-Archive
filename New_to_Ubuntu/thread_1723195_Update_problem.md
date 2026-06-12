---
title: "Update problem"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by duncan503 on 2011-04-06
Hello every time I update the system Ubuntu 10:04 I get the following message:

"GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 09266047CE9FDCA9Failed to fetch [http://ppa.launchpad.net/unity/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/unity/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead."

So What do I do to correct this problem?...

---

### Post by techunit on 2011-04-06
Remove the ppa from the source center in the Ubuntu Software Center.

---

### Post by duncan503 on 2011-04-06
> **techunit said:**
> Remove the ppa from the source center in the Ubuntu Software Center.

Thx But I cannot find the ppa in question.
Also is there a way to rebuild the **repositories**?

---

### Post by plucky on 2011-04-07
> **duncan503 said:**
> Thx But I cannot find the ppa in question.
Also is there a way to rebuild the **repositories**?

It should be located in /etc/apt/sources.list.d/

Please post output of ```
ls -l /etc/apt/sources.list.d/
```


Also,did you look under the "Other Software" tag in Software Sources?

---

