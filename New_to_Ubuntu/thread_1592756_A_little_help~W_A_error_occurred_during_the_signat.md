---
title: "A little help~W: A error occurred during the signature verification. The repository i"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by ALF102 on 2010-10-10
Tried to run sudo apt-get update && sudo apt-get upgrade, then this appear near the end of the list:


W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

What could this mean?

---

### Post by gareththered on 2010-10-11
Hi,

I reinstalled ubuntu-extras-keyring package and it got rid of this issue.

Hope it helps,

Gareth

---

