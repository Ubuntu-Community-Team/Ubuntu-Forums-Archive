---
title: "Installing/updating subversion problem"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by blindasfcuk on 2009-03-08
Hi Guys Im new to Linux so I thought Id get started with the easy option, ubuntu! Im trying to install a couple of servers and for the installation I need subversion. On my first attempt I tried svn and it wasnt installed so I tried:

sudo apt-get install subversion

I got the following error:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main libapr1 1.2.7-8.1
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main libpq5 8.2.3-3
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main libsvn1 1.4.3dfsg1-1ubuntu1
  404 Not Found [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main subversion 1.4.3dfsg1-1ubuntu1
  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apr/libapr1_1.2.7-8.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apr/libapr1_1.2.7-8.1_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.2/libpq5_8.2.3-3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.2/libpq5_8.2.3-3_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/subversion/libsvn1_1.4.3dfsg1-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/subversion/libsvn1_1.4.3dfsg1-1ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/subversion/subversion_1.4.3dfsg1-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/subversion/subversion_1.4.3dfsg1-1ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

When I try using firefox to find the individual files in feisty/main I get 404 not found but I can find the files under /ubuntu/dists/jaunty/main

Ive tried running sudo apt-get --fix-missing update
and Ive also tried switching my software sources server but that didnt work either. Im using Ubuntu (Feisty Fawn 7.04) as a virtual machine with vmware. Any help at all would be great!

---

### Post by taurus on 2009-03-08
Feisty has expired and the repos have moved, [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/).  Either install hardy (8.04) or replace the repos in /etc/apt/sources.list with **[http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu)**.

---

### Post by blindasfcuk on 2009-03-09
Nice one I installed the latest version and it works fine!

---

