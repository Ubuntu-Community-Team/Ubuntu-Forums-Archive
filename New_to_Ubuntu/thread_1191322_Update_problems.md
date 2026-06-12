---
title: "Update problems"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by Handyandy52 on 2009-06-18
How do I get rid of this problem with updating. Or do I need to reload.

  GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release](http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release)  Unable to find expected entry  multiversedeb/source/Sources in Meta-index file (malformed Release file?)

---

### Post by fooman on 2009-06-18
open a terminal and run this command:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0C5A2783
```

hope that helps.

---

### Post by nandemonai on 2009-06-18
Do a reload after that and you should be good. The second error was likely bad timing, the mirror may have currently been in the process of an update itself.

Add the medibuntu key, reload and try again. ;)

---

