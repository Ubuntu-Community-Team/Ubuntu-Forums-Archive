---
title: "install R enabling shlib for rpy2"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by nick@R on 2011-03-22
Hi,
 
Have installed Ubuntu packages for R by adding: 
deb http://<my.favorite.cran.mirror>/bin/linux/ubuntu hardy/
to my /etc/apt/sources.list file and using: 
sudo apt-get update
sudo apt-get install r-base
 
I see from a previous thread that to enable shlib I need to download source files to my home directory. When I run 
apt-get source r-base
I get the message: 
You must put some 'source' URIs in your sources.list
 
Fair enough! Does anyone out there know how I can do this? Dont they come with the instalation? :confused:
 
I can see then that, once I have the source, I just run:
apt-get source r-base
again and then:
./configure ./configure --enable-R-shlib 
(I already have X11 installed)
 
Sound correct?
 
Thanks a million!

---

