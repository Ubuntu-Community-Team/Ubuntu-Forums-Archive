---
title: "How to install VLC player in Ubuntu ?"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by akshatgamer on 2009-02-01
It is in a compressed tar.gz file,how to install it in Ubuntu,,,
(actually I want to know how to install it in Ubuntu,if you could tell me how to install them using VLC Player installation as an example)
Please don't tell me to use some package manager....only tar.gz

---

### Post by binbash on 2009-02-01
Dude you will untar it and try ./configure 

then make and sudo make install

---

### Post by arochester on 2009-02-01
Have a look at "How to install ANYTHING in Ubuntu!" on [http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

### Post by akshatgamer on 2009-02-01
Thanks

---

### Post by nj96 on 2009-02-01
You need to make sure that you have a “universe” mirror in your /etc/apt/sources.list

sudo apt-get update

sudo apt-get install vlc vlc-plugin-esd

This will complete the installation

If you want to open VLC You need to go to Applications—>Sound&Video—>VLC Media Player....
its real simple.. i did it and im only 11!

---

### Post by akshatgamer on 2009-02-01
But I want to install it from my tar.gz compressed folder,not from the net,,,,but thanks

---

