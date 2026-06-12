---
title: "jaunty update problem:beginner"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by nayanjha on 2009-09-15
I am using ubunty 9.04.(jaunty). I cant install packages
Following error occure while updating repository index

*Failed to fetch [http://ppa.launchpad.net/sugree/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages](http://ppa.launchpad.net/sugree/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages)  407 Proxy Authentication Required*

please help

---

### Post by earthpigg on 2009-09-15
hi,

this is sugree's launchpad page: [https://launchpad.net/~sugree](https://launchpad.net/~sugree)

somewhere along the line, you or another using your system with root privelages added his/her repository to your list of software sources.

let's go ahead and remove him from that list and give it a shot:

system -> admin -> software sources -> third party software -> uncheck the box that says 'sugree' somewhere next to it. now, run this:

> sudo apt-get update


and see if things are cleared up.

---

