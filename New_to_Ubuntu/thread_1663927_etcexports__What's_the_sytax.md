---
title: "/etc/exports  What's the sytax?"
date: 2011-01-10
forum: New to Ubuntu
---

### Post by Unewbeginner on 2011-01-10
Hello, I'm following the tutorial below to setup my shared folders.

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

I edited my exports file on my server as below:

```
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/share 192.168.1.3(rw, sync)
```

But after I typed 
```
sudo /etc/init.d/nfs-kernel-server restart
```

I got the message below:
```
exportfs: /etc/exports:1: syntax error: bad option list
```

What's the problem?

---

### Post by georgemc on 2011-01-10
This is so subtle that I could consider it a bug.
 

 Remove the spaces in the options, i.e.
 

 ```

 change from
 /share 192.168.1.3(rw, sync) 
to
 /share 192.168.1.3(rw,sync) 
``` When I add spaces to my /etc/export options and restart I get the same error message as you do when I  restart.


Hope this helps.


George

---

### Post by Unewbeginner on 2011-01-11
Thanks! it works now!

---

