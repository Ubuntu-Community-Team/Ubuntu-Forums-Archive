---
title: "Help with versions"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by Corelogik on 2009-05-15
I need some help in understanding the different versions of Ubuntu. I was browsing the [torrents]("http://torrent.ubuntu.com:6969/") list and I'm confused about which version is which, if someone could explain the differences to me, I would greatly appreciate it.

What I am looking to find out is how are 32-bit and 64-bit version differentiated from each other?

I know that 32-bit is i386. I am assuming that amd64 is 64-bit but there in lies the confusion. There are different designations, server, desktop, add-on, etc,.. depends on if you look for Ubuntu, Kubuntu, they're all different.

I am trying to figure out which one to download for the 64-bit, Desktop, version.

Can someone sort all of this out for me and tell which is which?

TIA

---

### Post by radiocognition on 2009-05-15
The core distribution is always identical for each Ubuntu distribution.  Each of the different versions adds on a few additional packages:

Ubuntu / Kubuntu / Xubuntu each use the GNOME / KDE / and XFCE desktop environments respectively.  Each of the install cd's for these versions can be run as a live CD - booting the entire OS into memory

Additionally there is a server version that is intended to quickly set up a server.  You can install server packages such as apache or mysql on any machine, but this version is stripped down to be fast & lean.  There is no xserver (gui & windows) installed by default and you can't use this as a live cd.

64-bit versions run on a 64-bit compatible processor and include libraries that are designed to run on this architecture.  There are performance boosts associated with using an optimized install. You guessed it 32 bits are for regular ol' computers

---

