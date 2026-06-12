---
title: "Errors installing Gnome desktop on Ubuntu Server 10.10"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by SeanKilleen on 2010-10-23
Hi all,

First post here, slightly new to Ubuntu Server / Linux in general.

I installed Ubuntu Server in VirtualBox (HostOS: Windows 7 x64, Guest OS Ubuntu Server 10.10 x64). I have bridged the network connection to my wireless adapter which currently has internet, so I can verify that it's at least got a connection.

I didn't set up the network configuration initially, so afterwards I modified the /etc/network/interfaces file to read the following:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

I also edited /etc/apt/sources.list to remove the comments for all repositories, which appears to include main and universe.

I run sudo apt-get update and it appears to update fine, except for extras, which says it can't be verified because the public key isn't available.

then, I run sudo apt-get install ubuntu-desktop (which I believe is the command for installing the GNOME desktop, but correct me if I'm wrong), and I get the error "Unable to locate package ubuntu-desktop".

What am I doing wrong? Be gentle, I'm new to the Linux game. :)

Thanks for any help you can give!

---

### Post by Chesamo on 2010-10-23
Can you post a copy of your sources.list? I can confirm that ubuntu-desktop exists in Maverick ([http://packages.ubuntu.com/maverick/ubuntu-desktop](http://packages.ubuntu.com/maverick/ubuntu-desktop)), so that shouldn't be the problem.

---

### Post by SeanKilleen on 2010-10-23
Finding it difficult to copy the text out of the sever screen through virtualbox to here. Any suggestions on how i can get it over to here w/o retyping? :)

FYI, it's the default sources.list for 10.10 -- just with all sources except backport uncommented.

---

