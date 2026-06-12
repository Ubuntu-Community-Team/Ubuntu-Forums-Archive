---
title: "Package Sharing on a Ubuntu server"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by K5-CJ5 on 2010-08-01
IS there a way to download programs and packages to a ubuntu server and store the files on that server to be utilized by other computers on the network, or write them to a cd?  I have a certain amount of downloads a month that I am able to do and would like to download the files once and distribute to my other desktops.

---

### Post by gordintoronto on 2010-08-01
Yes. You can download from packages.ubuntu.com, and the deb files can be installed on other computers. 

Note that many applications *depend* on other packages being installed first, thus the name dependencies. Also, a package is associated with a specific version of Ubuntu. You might run into grief installing a program on Karmic which is set up for installation on Lucid.

---

### Post by orethrius on 2010-08-01
I think the OP is referring to something like **rsync**ing from a private mirror, which I had working on Gentoo but never really took the time to figure out on Ubuntu.

---

