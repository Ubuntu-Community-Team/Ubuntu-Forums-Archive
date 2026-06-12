---
title: "OpenAFS on Ubuntu - Problem"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by n.l.o on 2007-02-11
Hi!

I've (I think at least) installed OpenAFS 1.4.2-4 client, module and Kerberos 5 integration, all according to 
this guide [http://doc.es.aau.dk/software/unixlinux/afs_on_linux/afs_on_ubuntu_610/]("http://doc.es.aau.dk/software/unixlinux/afs_on_linux/afs_on_ubuntu_610/").

I've also run the *dpkg-reconfigure openafs-client* command to set it up, and changed the chache dir to another partition of my harddrive which is not ReiserFS (ext3 instead).

But when i run *klog*, I get the following response (the response comes after a few seconds).

[I][INDENT]$ klog -principal <usr> -password <passwd> -cell su.se
Unable to authenticate to AFS because Authentication Server was unavailable.[/INDENT][/I]

When I try connecting to the same cell (su.se) through my client in windows, it works fine.
I have no idea what the problem is. Any help at all to search for whatever might be wrong with my settings is gladly appreciated.

I'm rather new to Linux...
I have Ubuntu Edgy Eft running on IBM/Lenovo Z61m.

Edit: I don't know if this is the right category to post this in, if it's wrong, I apologise.

/Magnus

---

