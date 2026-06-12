---
title: "SSH problem"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by merlinus on 2007-10-22
I had ssh working perfectly with feisty, but have run into several roadblocks with gutsy.

I use it to share folders and files across a LAN using static ip addresses on the three boxes.

openssh-server and ssh are installed and running on the machines.

Here is one of the error messages:
 WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
38:d9:5d:3c:ed:d3:0c:11:82:9f:2b:78:b8:77:3c:e1.
Please contact your system administrator.
Add correct host key in /home/merlin/.ssh/known_hosts to get rid of this message.
Offending key in /home/merlin/.ssh/known_hosts:1
RSA host key for 192.168.1.101 has changed and you have requested strict checking.
Host key verification failed.

Do I need RSA authentification, and if not, how can I disable the key request?

If so, then where in known_hosts should the new key be placed?

Many thanks!

---

### Post by merlinus on 2007-10-22
Think I may have resolved the problem by deleting /.ssh/known_hosts.

When I tried logging in to the remote machine, I got the RSA error message, but this time it volunteered to add the changed info to known_hosts, and I was able to access files and folders.

Seems it created a new known_hosts file, and now the problem has gone away.

---

