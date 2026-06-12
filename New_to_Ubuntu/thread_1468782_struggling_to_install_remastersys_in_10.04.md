---
title: "struggling to install remastersys in 10.04"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by sanitarium616 on 2010-05-01
i'm trying to install remastersys in 10.04 using:
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/ as the repository then:
sudo apt-get update
sudo apt-get install remastersys
but it comes up with:
W: Failed to fetch [http://www.remastersys.klikit-linux.com/repository/remastersys/Packages.gz](http://www.remastersys.klikit-linux.com/repository/remastersys/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
sanitarium@sanitarium-desktop:~$ sudo apt-get install remastersys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package remastersys
how can i fix this problem please
thanks sani

---

### Post by lkraemer on 2010-05-01
SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES -> OTHER SOFTWARE -> ADD

deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

SYSTEM -> ADMINISTRATION -> SYNAPTIC PACKAGE MANAGER

RELOAD, then ........
Search for remastersys, Mark, & Install

Ref:
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

lk

---

### Post by sr_guy on 2010-05-02
The site is dead. That's why it cannot be downloaded. 

I found a ppa repo that has it though:

deb [http://ppa.launchpad.net/yavdr/unstable-vdr/ubuntu](http://ppa.launchpad.net/yavdr/unstable-vdr/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/yavdr/unstable-vdr/ubuntu](http://ppa.launchpad.net/yavdr/unstable-vdr/ubuntu) lucid main

---

### Post by utkarshjadhav on 2011-10-18
> **sr_guy said:**
> The site is dead. That's why it cannot be downloaded. 

I found a ppa repo that has it though:

deb [http://ppa.launchpad.net/yavdr/unstable-vdr/ubuntu](http://ppa.launchpad.net/yavdr/unstable-vdr/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/yavdr/unstable-vdr/ubuntu](http://ppa.launchpad.net/yavdr/unstable-vdr/ubuntu) lucid main


I used these two ppa repos
```

deb [http://ppa.launchpad.net/yavdr/unstable-vdr/ubuntu](http://ppa.launchpad.net/yavdr/unstable-vdr/ubuntu) lucid main 
 deb-src [http://ppa.launchpad.net/yavdr/unstable-vdr/ubuntu](http://ppa.launchpad.net/yavdr/unstable-vdr/ubuntu) lucid main
```then

```

utk@utk-laptop:~$ sudo apt-get update

```the output was

```

Reading package lists... Done
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 272A2CE18103B360

```Please help with this.

---

