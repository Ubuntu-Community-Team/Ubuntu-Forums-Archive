---
title: "No wireless after system updates"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by AndyPopely on 2007-07-07
When you install system updates you may find that your wireless connection via ndiswrapper no longer works and you may even experience system hangs during the connection process.

This is often as a result of ndiswrapper needing to be recompiled.  The following is how to do this.

Locate the curent ndiswarpper tar that you last used or go get the latest stable version of ndiswrapper
[http://sourceforge.net/projects/ndiswrapper](http://sourceforge.net/projects/ndiswrapper)

Once it's on your system here's what to do

1. CD to the directory containing the tar file
2. tar -zxvf ndiswrapper-version.tar.gz
3. CD to the ndiswrapper directory that's been created
4. make distclean 
5. make
6. sudo make install

---

