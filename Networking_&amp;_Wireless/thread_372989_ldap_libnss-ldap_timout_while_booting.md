---
title: "ldap libnss-ldap timout while booting"
date: 2007-02-28
forum: Networking &amp; Wireless
---

### Post by kopus on 2007-02-28
Hi all,

I have configured an ldap server using debian etch and I'm suppling nfs home's and authentication to edgy clients.

I have the following configurations:

nsswitch.conf
```
passwd:         files ldap
Group:          files ldap
shadow:         files ldap
...
```

The configuration goes like this, it works although when I do the command 'getent group' it does not list the ldap groups.  If I change the nsswitch.conf to this

```
passwd:         files ldap
group:          files ldap
shadow:         files ldap
...

```
It lists the groups fine but I get timeouts while booting.

```

udevd[2004]: nss_ldap: could not connect to any LDAP server as (null) - Can't contact LDAP server
udevd[2004]: nss_ldap: failed to bind to LDAP server ldap://10.x.x.x: Can't contact LDAP server
udevd[2004]: nss_ldap: reconnecting to LDAP server (sleeping 16 seconds)...

```

Does any one have an idea of what is causing this?

---

### Post by hayalci on 2007-03-24
see the bug report here, you are lucky that your system actually booted, mine didn't :)

[https://launchpad.net/ubuntu/+source/libnss-ldap/+bug/51315](https://launchpad.net/ubuntu/+source/libnss-ldap/+bug/51315)

---

### Post by kalariwarrior on 2007-05-04
After MUCH research and frustration, here are the steps that worked for me:

*** FIRST THINGS FIRST *** If you can't get past this error (I couldn't), you will need to to live boot (let me learn some vi) and edit stuff or reinstall. Some people said they could cancel past the error or that it would time out but mine never let me. :confused: 

*** SECOND THINGS FIRST *** Make sure you have the latest libnss-ldap package. I just used whatever apt-get pulled down. Some people found upgrading solved the issue.

1. After you install the libnss-ldap packackage but BEFORE you reboot, you need to edit libnss-ldap.conf (in /etc for me) and set the Bind policy or bind_policy to Soft. 
I had to uncomment the line as well. This allows the comp to keep booting even though it can't find whatever LDAP server or thing it wants.

You should also edit nsswitch.conf so that it looks something like this:

passwd: files ldap
group: files ldap
shadow: files ldap

The important thing is that files is BEFORE ldap...otherwise if ldap errors out it won't get to files (which is the hard drive I take it).

Reboot. You will still get the error message but your comp will keep booting this time. To remove the error message all together...

2. Add the following group with this command: sudo addgroup --system nvram 

This is a confirmed bug in Ubuntu, see the bug link in the previous post for more details.

Some people seem to get away with just doing 2. but I kept locking up until I did 1. so I'm including that first!

best of luck :guitar:

---

### Post by J3tD0g on 2008-05-29
90% newbie here.  I have been experiencing the same problem ever since I had to do a hard reboot of the system.

My libnss-ldap is v 258.  I have updated my nssswitch.conf to:

passwd: files ldap
group: files ldap
shadow: files ldap

There is already an nvram group on my system.

The problem is still there!  Any advice would be appreciated, bearing in mind that I'm pretty new, though comfortable with most terminal commands.

Cheers

---

### Post by J3tD0g on 2008-05-30
Ok, kids, I figured it out.  There was a permissions problem.  The ldap.conf files and slapd.conf needed to the chowned to openldap:openldap.  Once I did this everything worked out.

---

