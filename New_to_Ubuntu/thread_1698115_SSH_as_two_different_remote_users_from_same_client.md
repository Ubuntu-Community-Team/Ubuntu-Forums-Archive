---
title: "SSH as two different remote users from same client"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by japhyr on 2011-03-01
Hello,

I have two accounts on a machine I want to SSH into.  One account is the standard administrative account, call it regularadmin.  I have ssh'd into the remote machine using this standard account, and set up a public key so I don't have to repeatedly enter my password.  The second account is really for scripts, call it scriptadmin.

How do I set up ssh for the second account?  If I try to use "ssh scriptadmin@ipaddress", I get a message "Permission denied (publickey)." I tried copying the .ssh file from regularadmin's home directory to scriptadmin's home directory, but that did not help.

---

### Post by geoffmcc on 2011-03-01
Sounds like password login has been disabled on ssh. Did you change PasswordAuthentication  to no in */etc/ssh/sshd_config* file.

or for some reason its trying to use a key and its not the right one. 

The error you mentioned is the error you got before copying over the .ssh folder? By the way, now that that its copied over that might cause problems going forward. 

also you can find out what type of auth is being used by using " ssh -v scriptadmin@ipaddress "

---

### Post by japhyr on 2011-03-01
> Sounds like password login has been disabled on ssh. Did you change PasswordAuthentication to no in */etc/ssh/sshd_config* file.

Thank you, that was exactly it.  After allowing password authentication again, I deleted the .ssh folders, and used ssh-copy-id to each user account on the remote machine, and everything is working fine now.

---

