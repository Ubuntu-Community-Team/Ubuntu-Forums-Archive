---
title: "Updating repositories in Hardy error"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by iamleaf on 2009-05-19
I get the following code when I try to update my repo. 

```
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634

```

I want to install Amarok Nightly in Hardy but I can't update the repositories in the first place and the amarok nightly package doesn't show up in Synaptic.

---

### Post by taurus on 2009-05-19
You need to install keys for both Medibuntu and ppa.launchpad.net repos.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

p.s.  If you are running hardy, how come you have a repo (ppa.launchpad.net) for intrepid?  Mixing repos in /etc/apt/sources.list is a real bad idea.

---

### Post by iamleaf on 2009-05-20
Thanks :)

---

