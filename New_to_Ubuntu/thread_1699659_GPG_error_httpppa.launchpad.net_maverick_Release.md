---
title: "GPG error: http://ppa.launchpad.net maverick Release"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by skey. on 2011-03-04
Hi Guys. I have tried to do update via "apt-get" and I get this "W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 48C18E890A02563F" Is there any-one can help? As I new to this I'm lost.

---

### Post by Dutch70 on 2011-03-04
[http://www.ubuntugeek.com/fix-for-gpg-error-httpextras-ubuntu-com-maverick-release.html](http://www.ubuntugeek.com/fix-for-gpg-error-httpextras-ubuntu-com-maverick-release.html)

[http://en.kioskea.net/faq/809-debian-apt-get-no-pubkey-gpg-error](http://en.kioskea.net/faq/809-debian-apt-get-no-pubkey-gpg-error)

---

### Post by sikander3786 on 2011-03-04
Try adding the missing GPG key.

Applications > Accessories > Terminal:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 48C18E890A02563F
```

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by skey. on 2011-03-04
Thanks Guy's, all fixed now. 
thanks for the quick reply's

---

