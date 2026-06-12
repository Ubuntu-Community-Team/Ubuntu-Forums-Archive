---
title: "NFS share takes very long to mount"
date: 2005-06-24
forum: Networking &amp; Wireless
---

### Post by knorr.orange on 2005-06-24
I have a server with an NFS share (running Fedora Core 1) and when I mount it from my primary machine (running Hoary 5.04), it takes about one minute.  This never used to be the case when I had Core2 or Core3 on the same machine.  Is there something I can change to have this NFS share mount faster?

Any suggestions are most appreciated.

---

### Post by nictuku on 2005-06-24
Can you check if your DNS is taking too long to resolve local names?

---

### Post by knorr.orange on 2005-06-25
Thank you for your suggestion nictuku.  It currently mounts via ip address, so I'm not sure that's the problem.  I suppose it could be trying to look up the ip as a name and timing out on that and then trying the ip.  Of course that is all just complete guessing.

What is the best way to test if it is taking too long to resolve a local name?  And if that's the problem, is there something I can do to fix it?

---

### Post by rhino on 2005-06-27
Make sure you have port map installed. I have seen this before and after installing portmap I could mount in <1 sec.

---

### Post by knorr.orange on 2005-06-28
That did it.  Thanks rhino!

---

