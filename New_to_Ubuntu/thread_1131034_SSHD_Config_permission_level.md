---
title: "SSHD_Config permission level"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by televisi on 2009-04-20
Hi All,
I'm hoping this my new thread is a new beginning of my Linux life ;)

I've configured my ssh in my Ubuntu 8.04.2 server edition, SSH seems working fine.

According to the documentation (man sshd_config)
> The allow/deny directives are proccessed in the following order: DenyUsers, AllowUsers, DenyGroups, and finally AllowGroups.

Now, I do testing using different user and groups, for example:
> 
- Group A
=> user A1
=> user A2

- Group B
=> user B1
=> user B2

- Group C
=> user C1


Now, I set /etc/sshd_config:
[B]AllowUsers A1 B1 C1
AllowGroups A[/B]

What I noticed is user [COLOR="Red"]**B1 C1 not allowed to login through SSH**[/COLOR] (after restart the service obviously), because user B1 & C1 not in **AllowGroups**, interesting eh?!

I also do some DEBUG1 testing and find out the permission level are as follow:
- AllowUsers  => lowest (this setting will be overridden with higher levels)
- AllowGroups 
- DenyGroups
- DenyUsers => highest

Do I miss something here?

---

### Post by Hospadar on 2009-04-20
What if you change it to 
**AllowGroups A**
**AllowUsers A1 B1 C1**

---

### Post by televisi on 2009-04-20
Same thing, it gives me error:
**[COLOR="Red"]User B1 from SERVER not allowed because none of user's groups are listed in AllowGroups[/COLOR]**

---

### Post by spiderbatdad on 2009-04-20
```
sudo usermod -a -G B1 A
sudo usermod -a -G C1 A
```

or AllowGroups A B C

---

### Post by televisi on 2009-04-20
Hi spiderbatdad,
I suspect by running above code (usermod), we include B1 & C1 to group A.

Will this make another issue though? especially in file permission? (ie: if I only want **group A to RW** to specific directory and **other (group B/C) with R permission only**)

Thanks

---

### Post by antikristian on 2009-04-20
I usually only use AllowGroups D
Create a new group D and add the users I want to be able to use SSH to group D

The other group permitions still apply though, if User A1 is member of group A and D, and a folder is RO to group A, then A1 will only be able to read that folder.

If user B1 is member of A, B and D, and group B has RW of the same folder, user B1 will have RW access. And lastly, if C1 is member of group C and D, and group C has no read or write of that folder, C1 will not be able to open the folder.

---

### Post by televisi on 2009-04-21
Hm... interesting workaround!!!

So...is anyone know why permission level are as follow:
- AllowUsers => lowest (this setting will be overridden with higher levels)
- AllowGroups
- DenyGroups
- DenyUsers => highest

Linux Manual error? (I don't think so...)

---

### Post by antikristian on 2009-04-23
According to the manpage it gets processed in this order:
> The allow/deny directives are processed in the following
             order: DenyUsers, AllowUsers, DenyGroups, and finally
             AllowGroups.

This is similar to how tcpwrapper does it:

If you set hosts.allow to ALL: ALL and hosts.deny to mycomp: ALL, then mycomp, and all other computers will get access (I belive). But if you set hosts.deny to ALL: ALL and hosts.allow to mycomp: ALL, then only mycomp will get access.

All in all, it comes down to a choice done by the developers, and doing it the other way around would probably have its advantages.

---

