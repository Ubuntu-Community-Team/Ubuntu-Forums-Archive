---
title: "How to fix this error"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by halovivek on 2011-01-28
How to fix this error in update manager?
W:Failed to fetch [http://debian.scribus.net/debian/dists/testing/Release](http://debian.scribus.net/debian/dists/testing/Release)  Unable to find expected entry  non-free/binary-amd64/Packages in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by conradin on 2011-01-28
Hm, look here:
[http://ubuntuforums.org/showthread.php?t=767811](http://ubuntuforums.org/showthread.php?t=767811)

---

### Post by halovivek on 2011-01-29
Now I am getting this.

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://debian.scribus.net/debian/dists/testing/Release](http://debian.scribus.net/debian/dists/testing/Release)  Unable to find expected entry  non-free/binary-amd64/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by supererki on 2011-01-29
For the first warning you have to add the key. Command should be something like :

wget [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

---

For the second warning - it seems that there is no 64-bit source available : Architectures: i386 source

Can you post the output of :
cat /etc/apt/sources.list |grep [http://debian.scribus.net/debian/dists/testing/Release](http://debian.scribus.net/debian/dists/testing/Release)

Anyhow - you can use 32bit software on 64bit architecture. 
for example you can use the --force-archidecture flag in dpkg

---

### Post by supererki on 2011-01-29
It seems i was wrong. There is 64bit version.

try to follow instructions from this site :

[http://wiki.scribus.net/canvas/Debian](http://wiki.scribus.net/canvas/Debian)

---

### Post by halovivek on 2011-04-01
hi 
I found out the solution for this. I went to package manager and removed the unwanted ones which I selected.
Now it is working fine.
Thank you all.:P

---

