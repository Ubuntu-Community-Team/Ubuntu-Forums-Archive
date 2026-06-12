---
title: "long delay for NFS mount"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by jinx099 on 2006-10-29
I have a network with a fileserver set up and I am having a problem with my NFS mounts between the server and my desktop.  The problem is that when I mount the nfs filesystem, there is a long delay, about 1 minute or more, between the time I mount and the time it is actually mounted.  This probelm just started recently, and I do not know what I changed for the problem to occur.  My fileserver is running openSUSE 10.1 and my desktop is running Edgy.  I also have openSUSE and fedora core 6 installed on my desktop so I will post back after I test mounts on those OSes.

I think the problem started about when I upgraded to edgy from dapper, but I am not sure.  Everything worked fine with dapper, and the fileserver's os has not changed.  I have also completely disabled the firewalll on the server, but it does not help.

Any ideas?

---

### Post by DaveBorealis on 2006-10-29
Hello,

When you upgraded did you lose the nfs-common and portmat packages?  After switching to Ubuntu, I was using NFS to mount directories and noticed a minute or two mounting delay (along with some other flakey behavior).  I installed the two packages, added info to /etc/hosts.allow and /etc/hosts.deny, and now when I mount three directories at once it happens within a second or two, and the weird behavior went away.

Best regards,
Dave

---

### Post by jinx099 on 2006-10-29
Thank you very much, that seemed to be the problem.  I just installed nfs-common and portmap was installed as well and the problem is gone.

Thanks!

---

