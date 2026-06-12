---
title: "Likewise - next steps"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by inselaffe on 2008-04-24
I've tried AD authentication in the past and mostly given up as it was just too difficult to be worth the benefits. So I was interested to see how Likewise would function in Hardy.

Joining the AD turned out to be painless, as is logging on as a domain user.

I now want to switch from using a local user to my domain account primarily, just to keep things consistent. I also want to configure the level of access other domain users have to my workstation. But how do I add domain users to groups?

Domain users do not feature in the Users and Groups applet, and usermod returns:
```
usermod: domain\username not found in /etc/passwd
```

---

### Post by RipTorn on 2008-06-16
I'm pretty much having the same problem, I can try to add the DOMAIN+user.name to /etc/group manually but it doesn't seem to work for things like samba.

e.g.

I want to be able to create a new 'local' group on the Linux server and add a domain user to this group. so I have created 'testgroup' and tried adding a user in /etc/group as a member so...

```
testgroup:x:13664:DOMAIN+user.name
```

and when I set permissions on a local share in samba to only allow people part of the local group 'testgroup' to access the file it fails because it doesn't seem to think DOMAIN+user.name can be part of a local group created locally. 

Where if I create a localuser called user.name and create a local samba account with the same username and password as on the domain it works. This isn't obviously ideal as I have a few hundred people trying to access the shares.

I'm obviously not that great at explaining things but it makes sense in my head ;)

-Rip

---

### Post by likeWiseGuy on 2008-10-01
> **inselaffe said:**
> I've tried AD authentication in the past and mostly given up as it was just too difficult to be worth the benefits. So I was interested to see how Likewise would function in Hardy.

Joining the AD turned out to be painless, as is logging on as a domain user.

I now want to switch from using a local user to my domain account primarily, just to keep things consistent. I also want to configure the level of access other domain users have to my workstation. But how do I add domain users to groups?

Domain users do not feature in the Users and Groups applet, and usermod returns:
```
usermod: domain\username not found in /etc/passwd
```

Hi inselaffe & Rip,

I hope I'm not too late in helping out with your ubuntu active directory integration. 

The simplest way to add domain users in local groups is to add the domain users in the form of "DOMAIN\username" in your /etc/group file. I just tried it out and it worked for sudo:

```
root:x:0:DOMAIN\user.name
```

then in /etc/sudoers
```
%root ALL=(ALL) ALL
```

If the domain in the /etc/group file is all lower-case, sudo would deny the domain user any privileges. So make sure to be case-sensitive. Also note that dots "." in the username worked for me as above.

Let me know if this works out for you.

Thanks.

---

### Post by wolfteeth on 2009-09-07
it realy works. many thanks....

---

