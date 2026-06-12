---
title: "YASQ - Yet another Samba Question"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by volksman on 2007-06-11
Hey All!

I've been using Feisty and Samba since Feisty came out.  Fresh installs on all my machines.  I have three machines using Feisty.

Last night I noticed that all of a sudden my xbox couldn't browse the Samba shares on my network (none of them).  So I started looking into it today and found this:

On 1 of 3 machines if I run smbtree I get only a response from the local machine but not any of the others.  The other 2 just return me to a command prompt after running smbtree.

On all three boxes if I run findsmb they find all the neighbors.

On one box the version is 3.0.22 the other two 3.0.24 however the one box says it is up to date and will not patch to 3.0.24.

I have no windows boxes left on the network but as mentioned the Xbox uses samba so I need it.

Any ideas?  This is seriously driving me crazy!

---

### Post by volksman on 2007-06-11
smbclient -L to all machines also replies correctly with the information on the shares that machine is setup with.  This is really weird...I don't know what else to check....

---

### Post by volksman on 2007-06-11
So here's the answer:

local master = Yes
preferred master = Yes

Put that in one of my smb.conf files and restarted samba on the machine and presto.  Samba restored.

---

