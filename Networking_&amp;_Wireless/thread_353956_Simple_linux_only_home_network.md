---
title: "Simple linux only home network"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by renzokuken on 2007-02-05
Hi,

I have a desktop and a laptop at home both using Ubuntu.

I want to be able to access files on one from the other, share folders etc, as in a small windows network.

I.m not sure how though. Do i use samba or NFS or something? I've used samba when a windows pc is involved but never used NFS. I've never done it linux only, and i'm not sure if i'm reading the correct howto's.

Any advice/input is greatly welcome.

Thanks

---

### Post by newlinux on 2007-02-05
I personally use samba (I still have one XP dual boot machine). I think samba might offer a little more flexibility at the cost of more complicated setup. NFS should be a bit easier to setup in an all Linux environment, but I haven't actually done it so I can't say for sure. If you ever plan on having windows clients I would definitely recommend Samba. You can also look into to using sshfs if security is a big issue.

---

### Post by jimcooncat on 2007-02-05
If you're using ssh to log in and maintain your other machines, sshfs is the way to go to keep things simple. If you need to add a Windows machine then install WinSCP on that to retrieve files, as well as [http://sshwindows.sourceforge.net/](http://sshwindows.sourceforge.net/) to serve the files. 

I haven't got the hang of sharing printers with CUPS, and I still use SAMBA for that. I ought to learn the right way, though.

---

### Post by linuxyousertoetags on 2007-02-05
hey im having the same problem i have 2 computers running dapper and the both can connect to the internet with the router hooked up. i just dont know how to share files and other devices through the 2 computers if anyone knows anything please let me know

---

### Post by dmizer on 2007-02-05
samba is slow, flaky, and difficult to configure.  ssh/fuse (sshfs) have problems too (like not being able to access the remote files directly).  sshfs is also slow.

if you want an all linux network, use nfs ... howto can be found in the 4th link in my sig.  takes all of about 10 minutes to set up.

nfs is written for linux file sharing and is fast and stable.  however, i don't believe it's possible to share network devices (like printers) with nfs.

---

### Post by renzokuken on 2007-02-06
thanks dmizer, i'll have a go tonight.

i tried samba last night but it was slow and unpredictable as you say. fortunately i dont need to share printers either, although i guess there is always cups for that.

thanks, i'll let u know how it goes.

---

