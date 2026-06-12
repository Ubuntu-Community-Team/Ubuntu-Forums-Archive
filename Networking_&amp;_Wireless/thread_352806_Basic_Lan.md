---
title: "Basic Lan"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by Michiba on 2007-02-03
Hi all,

I have a hard wired network that all works fine using the internet etc. I want to use basic lan  just to copy files from one pc to another. When I had a windows pc hooked up this was easy enough to do with samba. I no longer want to run windows, even for file transfer.

So to get one ubuntu PC to access another PC Hard disk with a simple hard wired Lan connection is all I want to do. 

Do I need to set up one PC as a server? There dosent seem to be a simple network set up between machines?

Thanks 

Michiba

---

### Post by gradedcheese on 2007-02-04
You can just use samba as before, create shares in the System->Administration->Shared Folders tool and then browse for them in Places->Network Servers.  If it's just Linux PCs, you can also use NFS (which is more normal for Linux LANs), the Shared Folders tool also lets you set that up.

If you want to just transfer a file or two between PCs without all the overhead of shares and browsing, you can install openssh-server and openssh-client on each PC and then use 'scp'.

---

