---
title: "Downloading programs NOT in ubuntu software center"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by LadySapphira on 2010-02-27
There are a few programs I want to install from other sites.


My problem is when I download them, I get the files but don't know what to do with them *hides*

I can open the "install" part of the file but I can't manage to run it.
What do I do?  Is there something I have to type into the terminal??

I really prefer ubuntu to windows but there's a program I need for school that I I want to get working on ubuntu (cisco vpn client)

---

### Post by HermanAB on 2010-02-27
Hmm, you need to install the kernel headers using Synaptic and then you need to compile from source with something like:
tar -zxvf file.tgz
cd file
./configure
make
sudo make install

---

### Post by ikt on 2010-02-27
> **LadySapphira said:**
> There are a few programs I want to install from other sites.


My problem is when I download them, I get the files but don't know what to do with them *hides*

I can open the "install" part of the file but I can't manage to run it.
What do I do?  Is there something I have to type into the terminal??

I really prefer ubuntu to windows but there's a program I need for school that I I want to get working on ubuntu (cisco vpn client)

Have you tried this?:

[http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/](http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/)

---

