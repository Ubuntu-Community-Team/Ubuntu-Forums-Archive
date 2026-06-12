---
title: "installing g++ in ubuntu 10.04"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by ceejay724 on 2010-08-17
Good Day 

I am having trouble putting g++ on ubuntu

I used: "sudo apt-get install g++"

And the output was as follows:
[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  g++-4.4 libstdc++6-4.4-dev
Suggested packages:
  g++-multilib g++-4.4-multilib gcc-4.4-doc libstdc++6-4.4-dbg
  libstdc++6-4.4-doc
The following NEW packages will be installed:
  g++ g++-4.4 libstdc++6-4.4-dev
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,443kB of archives.
After this operation, 21.3MB of additional disk space will be used.
[COLOR=Red]Do you want to continue [Y/n]? y[/COLOR]
WARNING: The following packages cannot be authenticated!
  libstdc++6-4.4-dev g++-4.4 g++
[COLOR=Red]Install these packages without verification [y/N]? y[/COLOR]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main libstdc++6-4.4-dev 4.4.3-4ubuntu5
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main g++-4.4 4.4.3-4ubuntu5
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main g++ 4:4.4.3-1ubuntu1
  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/libstdc++6-4.4-dev_4.4.3-4ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/libstdc++6-4.4-dev_4.4.3-4ubuntu5_i386.deb)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/g++-4.4_4.4.3-4ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/g++-4.4_4.4.3-4ubuntu5_i386.deb)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.4.3-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.4.3-1ubuntu1_i386.deb)  407  Proxy Authentication Required
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

[/B]HOW DO i AUTHENTICATE THESE PACKAGES?

---

### Post by john newbuntu on 2010-08-17
Typically to install g++/gcc, try:
sudo apt-get install build-essential

Also, query this in google b4 posting it since it has been asked several times b4.

---

### Post by ceejay724 on 2010-08-17
I did the whole "sudo apt-get install build-essential" thing and got a similar output. The problem is with the [COLOR=SeaGreen]**Proxy Authentication Required**[/COLOR] part. How do I do the authentication?

---

### Post by ubudog on 2010-08-17
Maybe this thread will help you: [http://ubuntuforums.org/showthread.php?t=400210](http://ubuntuforums.org/showthread.php?t=400210)

---

### Post by ceejay724 on 2010-08-17
Thank you guys

I am still having some problems though
Will try and fight through it, and get back to you guys

---

