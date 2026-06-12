---
title: "[SOLVED] Nautilus - Host key verification failed"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by jimmy the saint on 2008-12-28
I am trying to connect to my server through nautilus' "connect to server" with the ssh option.  I get an error box that says
```
Can't display locations "sftp://bluto@192.168.211.10/"
Host key verification failed
```

I have webmin installed.  I can ssh in through putty.  I have proftp installed and I can login via gftp.  

How can I fix this?

---

### Post by jimmy the saint on 2008-12-28
apparently when the server was reinstalled, the ssh key changed.  Rather than ask if that is ok, Nautilus simply refuses to connect.  I renamed the ~/.ssh/known_hosts file to ~/.ssh/known_hosts.old and that solved the problem.

---

### Post by baisong on 2011-03-30
Thanks a ton, this fixed it for me too!

For me, this happened when I changed my domain to another hosting service.

---

