---
title: "looking for an easy way to tell hosts in know_hosts"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by paradoxbound on 2008-06-19
In RHEL systems it is easy to tell which host is which in the ~.ssh/know_hosts file as they prepend the host name. Does anyone know how to make this happen with Ubuntu?

Also can someone recommend a way of easily recognizing the correct key in the file?

Thanks

---

### Post by jetsam on 2008-06-19
> Does anyone know how to make this happen with Ubuntu?

This is from the ssh_config man page:
```
     HashKnownHosts
             Indicates that ssh(1) should hash host names and addresses when
             they are added to ~/.ssh/known_hosts.  These hashed names may be
             used normally by ssh(1) and sshd(8), but they do not reveal iden&#8208;
             tifying information should the file&#8217;s contents be disclosed.  The
             default is &#8220;no&#8221;.  Note that existing names and addresses in known
             hosts files will not be converted automatically, but may be manu&#8208;
             ally hashed using ssh-keygen(1).  Use of this option may break
             facilities such as tab-completion that rely on being able to read
             unhashed host names from ~/.ssh/known_hosts.

```

The default on Debian and Ubuntu is "HashKnownHosts yes" for security reasons.  If you're comfortable with the security implications of changing this, you can edit your ssh config:
```
gksu gedit /etc/ssh/ssh_config
```
and change ```
HashKnownHosts yes
``` to ```
HashKnownHosts no
```

Already known hosts won't be regenerated, though, so you'll probably want to delete or move your known hosts file:
```
mv ~/.ssh/known_hosts ~/.ssh/known_hosts.old
```
Then they'll get regenerated the next time they're needed only now with their hostnames and ip address info in the known hosts file.

---

