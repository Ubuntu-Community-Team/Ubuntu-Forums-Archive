---
title: "What does CD to folder mean here?"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by k_squired on 2009-06-07
1.1 Install OIS
Go to OIS's download's page: [http://sourceforge.net/project/showfiles.php?group_id=149835](http://sourceforge.net/project/showfiles.php?group_id=149835) and download the latest release. Decompress the file, open a terminal window, and cd to the decompressed folder. Then, in a rather particular order, type:
./bootstrap
./configure
make
sudo make install

---

### Post by mgt_90 on 2009-06-07
&quot;cd&quot; is a command you run in the Terminal which changes the directory you're in. Change directory, hence the name: cd.  So when you extract the tarball and get a folder, open up a terminal, type "cd" followed by the name of the folder, and then run the rest of the commands to compile it.

---

### Post by k_squired on 2009-06-07
Thanks.  And what do bootstrap and configure mean?

---

### Post by lisati on 2009-06-07
> **k_squired said:**
> Thanks.  And what do bootstrap and configure mean?

They are commands that help complete the installation.

Edit: further reading: [http://en.wikipedia.org/wiki/Bootstrap](http://en.wikipedia.org/wiki/Bootstrap) and [http://en.wikipedia.org/wiki/Configure](http://en.wikipedia.org/wiki/Configure)

---

