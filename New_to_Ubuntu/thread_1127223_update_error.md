---
title: "update error"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by crabclaw on 2009-04-16
every time I try to update I get the following error message:

[INDENT]W: GPG error: [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ECDCAD72428D7C01
W: GPG error: [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ECDCAD72428D7C01
W: GPG error: [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ECDCAD72428D7C01
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783[/INDENT]


Am not entirely sure what I've done in the past to merit such horror... What can I do to fix this?

thanks

---

### Post by CLomax on 2009-04-16
```
wget -q [http://ddebs.ubuntu.com/dbgsym-release-key.asc](http://ddebs.ubuntu.com/dbgsym-release-key.asc)
sudo apt-key add dbgsym-release-key.asc
```

I wouldn't try this until someone else comes along with a reason not to... :p

---

### Post by nandemonai on 2009-04-16
> **crabclaw said:**
> Am not entirely sure what I've done in the past to merit such horror...

You didn't install the key.

"Most software repositories use a GPG key to digitally sign the files they provide, which makes it easy to check that the files have not been tampered with since their creation. In order for apt to be able to check this, you need the public key that corresponds to the signatures. The key should be available for download on the repository's website."

[https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html](https://help.ubuntu.com/8.04/add-applications/C/extra-repositories-adding.html)

---

### Post by llamabr on 2009-04-16
Right.  So this time, go back and add the keys.  Putting the repository in is a two part process, adding the line to your sources.list and adding the keys.  Here's the instructions for the medibuntu:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

You can generalize for the other one.

---

### Post by crabclaw on 2009-04-16
That's brilliant. Sorry I didn't thank anyone earlier, was at work without computer access.

thanks :)

crabclaw

---

### Post by CLomax on 2009-04-16
For others coming to this thread with the same problem, whose solution was the one that worked?

---

### Post by crabclaw on 2009-04-22
Clomax's reply worked perfectly.

Many many thanks:)

crabclaw

---

