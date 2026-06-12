---
title: "[SOLVED] Computers can't see each other."
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by P . P . L . on 2008-10-16
Hi i hope someone can help with this, I have two computers running Ubuntu 8.04 connected to a 8 port ethernet 

switch going to a ADSL modem both can get on the net no problem. I was told to use ssh to share files & for backups 

when i try to connect, this is the error message i get in a box. Same message on both but for the computer name.


(Couldn't display "sftp://peter@black-p4-3e/", because the host could be found.

Check that the spelling is correct and that your proxy settings are correct.)


I also have fire starter installed if that makes a differance, no one has been able to to help so far

any ideas.

pete.

---

### Post by Agent ME on 2008-10-16
Try using the IP address instead of the host name - use the command "ifconfig" to see what your computer's IP is set to.

Make sure you can ping the machines from each other. Also make sure you have openssh-server installed on the systems you want to be able to connect to.

---

### Post by Patb on 2008-10-16
Also Peter, if it's of any use, a useful Australian has written a useful guide to ssh at:
[http://users.bigpond.net.au/hermanzone/p11.htm](http://users.bigpond.net.au/hermanzone/p11.htm)

Cheers, Pat.

---

### Post by P . P . L . on 2008-10-16
Thanks for the replies, agent me's idea on i.p addresses got me thinking

all it took was to add the i.p addresses of each computer to fire 

starter's policy now all is well.

thanks again.

pete.

---

