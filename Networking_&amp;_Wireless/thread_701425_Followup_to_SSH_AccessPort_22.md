---
title: "Followup to SSH Access/Port 22"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by drmynatt on 2008-02-19
Hi group,  I loaded .ssh and verified port 22 is open. Now, when then remote person is trying to access the machine he receives this message:

 <Neo.210>% ssh jim@67.165.196.241
jim@67.165.196.241's password:
Permission denied, please try again.
jim@67.165.196.241's password:
Permission denied, please try again.
jim@67.165.196.241's password:
Permission denied (publickey,password).

I verified I have a authorized_keys file, and added his credentials to it into his user directory 
~jim

Have I missed something else?

Thanks,

Dave

---

### Post by tehet on 2008-02-19
On my Debian box I've got a line in /etc/ssh/sshd_config that says:
```
AllowUsers bla foo bar
```
which means that only the users bla, foo and bar are allowed to connect through ssh. You may need to add jim to that.

For trouble shooting you could look at /var/log/auth.log. non-AllowedUsers will show up as follows:
```
Feb 18 22:22:54 localhost sshd[6866]: Invalid user test from 222.192.176.2
Feb 18 22:22:55 localhost sshd[6868]: Invalid user guest from 222.192.176.2
Feb 18 22:22:57 localhost sshd[6870]: Invalid user admin from 222.192.176.2
Feb 18 22:22:58 localhost sshd[6872]: Invalid user admin from 222.192.176.2
Feb 18 22:23:00 localhost sshd[6874]: Invalid user user from 222.192.176.2
```

---

### Post by HermanAB on 2008-02-19
For debugging enable verbose error messages:
ssh -vvv joesoap@server

that'll tell you exactly what is wrong.

---

