---
title: "sudo apt-get update error"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by mvalviar on 2009-05-24
Whenever I run ```
sudo apt-get update
``` I get 
```

Reading package lists... Done
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: You may want to run apt-get update to correct these problems

```

in the end. Of course when I run apt-get update again it doesn't correct the problem but just displays the same error. How can I fix this?

---

### Post by Paulo39 on 2009-05-24
Did you try to add the public key for that repository?
Just see this: [https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)
there you can get help about how to add public keys to your system.

---

