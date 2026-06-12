---
title: "NFS4 write permission"
date: 2015-01-29
forum: Networking &amp; Wireless
---

### Post by ras123 on 2015-01-29
Hi,
I mounted using NFS4, but my user id is different in server and client, so that I cannot change files (write, delete). How can I solve this? I don't need to give read/write privileges for the root user in client but need to give read/write to a normal user, possible?
Regards
Ras

---

### Post by bab1 on 2015-01-29
> **ras123 said:**
> Hi,
I mounted using NFS4, but my user id is different in server and client, so that I cannot change files (write, delete). How can I solve this? I don't need to give read/write privileges for the root user in client but need to give read/write to a normal user, possible?
Regards
Ras
I would change the uid of the user on the client machine to match the uid on the server.  See the man pages for *usermod*```
man usermod
```

The usage on the client machine will be something like this```
sudo usermod -u <revised_UID_number> <username> 
```

[COLOR="#0000FF"]Edit:  Out of habit I match all of my users UID's across my home network rather than setup centralized user management.  I only have 4 users so it's not real time consuming.[/COLOR]

---

### Post by ras123 on 2015-01-29
Thanks, but I will lost ownership of current files. Is any possibility to userid mapping?

---

### Post by bab1 on 2015-01-29
> **ras123 said:**
> Thanks, but I will lost ownership of current files. Is any possibility to userid mapping?

The file ownership is easily changed by the sudo user (root).  You can use chown to do that.  Here is the incantation```
sudo chown <user>:<user-group> <file>
```
See the man pages for *chown*```
man chown
```

The permissions can also be changed using *chmod* ```
man chmod
```.

As an administrator you have complete control over all of this using sudo.  You will be better off using the tools correctly.  That way you won't be constantly fiddling with ownership and permissions issues.

---

