---
title: "Software Center error"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by nikhil-yelleswarapu on 2011-06-12
Hello,

I was trying to install WINE to support iTunes on Ubuntu. I tried to search for it in USC, but it did not show me anything. I tried to remove USC but this is the message I got,

sudo apt-get remove software-center
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Can anyone tell me what's going on?

Thank you

---

### Post by wolfen69 on 2011-06-12
Open a terminal and copy & paste the following:
```
sudo rm /var/lib/apt/lists/* -vf
```
then
```
sudo apt-get update
```

---

