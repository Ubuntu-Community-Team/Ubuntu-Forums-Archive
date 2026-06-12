---
title: "SSH Tunnels"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by russell.h on 2008-03-09
I am working on a set of perl scripts, one of which needs to connect to the other through via the internet.

The problem is that the one that needs to be connected **to** will be run on my laptop which has a dynamic IP. The good news is that the one that will be running on the machine opening the connection only needs to run when I have am sshed into that machine.

In short, if I run both scripts locally they work fine. But when I put the one that needs to be sending me information onto the remote machine, and do this:
```
ssh -R 9999:localhost:9999 name@host 
``` (but with name and host filled in) it never manages to open the connection.

Also, if I simply open the connection as above, then try to run them both locally it still won't work.

Can someone help me out here?

Thanks,

Russell

Edit: To be clear, ssh manages to run just fine, its the perl script that never manages to connect.

---

### Post by banewman on 2008-03-09
You might get better help posting in the programming talk forum.
Since it is a perl script issue.
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)
:)

---

### Post by russell.h on 2008-03-09
The thought occurred to me, but really its not an issue with the scripts, they work fine as long as they're running on the same machine, its the ssh tunnel that messes things up.

---

