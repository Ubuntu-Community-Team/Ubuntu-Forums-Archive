---
title: "error in terminal - signatures couldn't be verified"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by al.adab on 2009-07-02
hello,

after a fresh installation of Ubuntu 9.04 I followed directions given to enable the medibuntu repository (looks like I wasn't successful). I now keep getting this error in terminal

"Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems"

I tried to run sudo-apt get update + reload the update manager but the error is still there. What shall I do? Thanks.

---

### Post by Elfy on 2009-07-02
Try this

```
sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

