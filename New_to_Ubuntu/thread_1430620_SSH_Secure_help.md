---
title: "SSH Secure help"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by iamgeniusrnti on 2010-03-15
I was following the guidelines found here:

[http://www.linuxquestions.org/questions/linux-security-4/how-to-secure-ssh-in-ubuntu-and-slackware-552275/](http://www.linuxquestions.org/questions/linux-security-4/how-to-secure-ssh-in-ubuntu-and-slackware-552275/)

Purpose was to secure my ssh as much as possible so I could use my Droid to connect to my Ubuntu box.  There was one step where they tell you to chmod 600 the authorized keys file.  I did that and I lost my ability to log in with my pub/priv key.

I changed it to chmod 644 and it started working again.

What permissions should I be using??

This guys says 400; but I imagine that wont work either??
[http://joey.ubuntu-rocks.org/blog/2008/06/08/ssh-authorized_keys-permissions-or-why-ssh-is-smarter-than-you/](http://joey.ubuntu-rocks.org/blog/2008/06/08/ssh-authorized_keys-permissions-or-why-ssh-is-smarter-than-you/)

---

### Post by rnerwein on 2010-03-15
hi
the permissions "rw- --- --- ( 600 ) " for the authorized keys are correct.
but have a look at your ~/.ssh those permissions should be "drwx --- --- " too.
for debuging you can use: ssh -v user@remote_host.
ciao

---

