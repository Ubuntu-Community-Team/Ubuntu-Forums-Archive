---
title: "error downloading updates"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by denizente on 2011-02-19
Hi,

Am getting following when allowing updates:

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".

 I run Update Manager check and get:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://deb.opera.com](http://deb.opera.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8

W: Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


All suggestions welcome - thanks

---

### Post by fabricator4 on 2011-02-19
Ha, I came across an almost identical post today, already solved. [Have a look]("http://ubuntuforums.org/showthread.php?t=1258545&highlight=no_pubkey")

Chris

---

### Post by Frogs Hair on 2011-02-19
The opera key is out dated and a new key was issued with 11.01 . Make sure you have the latest version , and remove the old key from Update Manager > Settings > Other Software.

---

