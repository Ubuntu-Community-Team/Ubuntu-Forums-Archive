---
title: "not sure this error from repository"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by MeTylerDurden on 2010-04-14
: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810Failed to fetch [http://deb.torproject.org/torproject.org/dists/karmic/deb-src/binary-amd64/Packages.gz](http://deb.torproject.org/torproject.org/dists/karmic/deb-src/binary-amd64/Packages.gz)  404  Not Found [IP: 86.59.21.36 80]
Failed to fetch [http://deb.torproject.org/torproject.org/dists/karmic/http://deb.torproject.org/torproject.org/binary-amd64/Packages.gz](http://deb.torproject.org/torproject.org/dists/karmic/http://deb.torproject.org/torproject.org/binary-amd64/Packages.gz)  404  Not Found [IP: 86.59.21.36 80]
Failed to fetch [http://deb.torproject.org/torproject.org/dists/karmic/karmic/binary-amd64/Packages.gz](http://deb.torproject.org/torproject.org/dists/karmic/karmic/binary-amd64/Packages.gz)  404  Not Found [IP: 86.59.21.36 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by nothingspecial on 2010-04-14
```
gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -
sudo apt-get update
```

---

### Post by tom.swartz07 on 2010-04-14
> **MeTylerDurden said:**
> : The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810Failed to fetch [http://deb.torproject.org/torproject.org/dists/karmic/deb-src/binary-amd64/Packages.gz](http://deb.torproject.org/torproject.org/dists/karmic/deb-src/binary-amd64/Packages.gz)  404  Not Found [IP: 86.59.21.36 80]
Failed to fetch [http://deb.torproject.org/torproject.org/dists/karmic/http://deb.torproject.org/torproject.org/binary-amd64/Packages.gz](http://deb.torproject.org/torproject.org/dists/karmic/http://deb.torproject.org/torproject.org/binary-amd64/Packages.gz)  404  Not Found [IP: 86.59.21.36 80]
Failed to fetch [http://deb.torproject.org/torproject.org/dists/karmic/karmic/binary-amd64/Packages.gz](http://deb.torproject.org/torproject.org/dists/karmic/karmic/binary-amd64/Packages.gz)  404  Not Found [IP: 86.59.21.36 80]
Some index files failed to download, they have been ignored, or old ones used instead.

Run this and see how it works.

```
gpg --keyserver keyserver.ubuntu.com --recv 74A941BA219EC810
```
Then run this:
```
gpg --export --armor 74A941BA219EC810 | sudo apt-key add -
```

Then try your updates again

---

### Post by DestructionsRightHand on 2010-04-30
I am also still getting the same error after trying all the above steeps.  I am running x64 10.4.  Not sure if that makes a difference sense it cant hit the ip(s)

---

### Post by oldos2er on 2010-04-30
Run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
```

where KEYID is the number shown in error msg.

---

### Post by tom.swartz07 on 2010-04-30
> **oldos2er said:**
> Run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
```

where KEYID is the number shown in error msg.

Thats just what we told him to do previously.

It might be the case that the repo is offline and not available. Perhaps try looking up the information of the torproject repo and making sure that it is correct/available?

---

### Post by oldos2er on 2010-04-30
It appears [http://deb.torproject.org/torproject.org/dists/karmic/deb-src/binary-amd64/Packages.gz](http://deb.torproject.org/torproject.org/dists/karmic/deb-src/binary-amd64/Packages.gz) has changed to [http://deb.torproject.org/torproject.org/dists/karmic/main/source/Sources.gz](http://deb.torproject.org/torproject.org/dists/karmic/main/source/Sources.gz)

---

### Post by tom.swartz07 on 2010-04-30
> **oldos2er said:**
> It appears [http://deb.torproject.org/torproject.org/dists/karmic/deb-src/binary-amd64/Packages.gz](http://deb.torproject.org/torproject.org/dists/karmic/deb-src/binary-amd64/Packages.gz) has changed to [http://deb.torproject.org/torproject.org/dists/karmic/main/source/Sources.gz](http://deb.torproject.org/torproject.org/dists/karmic/main/source/Sources.gz)

Perfect! OP- just update your sources list from the system>sdministration>software sources app.

remove the old one for torproject and add the new one, then youre all set!

---

