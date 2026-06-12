---
title: "how do i login as root?"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by terryleon on 2009-05-29
Any help would be greatly appreciated

terryleon@hannah-the-dog:~$ adduser terryleon admin
adduser: Only root may add a user or group to the system.
terryleon@hannah-the-dog:~$ sudo -s
[sudo] password for terryleon: 
terryleon is not in the sudoers file.  This incident will be reported.
terryleon@hannah-the-dog:~$ sudo passwd root
[sudo] password for terryleon: 
terryleon is not in the sudoers file.  This incident will be reported.
terryleon@hannah-the-dog:~$

---

### Post by _Purple_ on 2009-05-29
If terryleon is your admin account, check the following link 
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by lisati on 2009-05-29
Is this your main admin account that you are using?

Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

edit: p.s. It might be easier to use the System->Administration->Users&Groups menu item

---

