---
title: "Set samba path = /"
date: 2016-01-15
forum: Networking &amp; Wireless
---

### Post by Raymond Day on 2016-01-15
I just want my samba to go to every thing so put the path = /

Don't want a password on it ether.

It seems like there is no way to do it. I can go to the / but any folder after that Windows all ways says: is not accessible. You might not have permission to use this network resource... The handle is invalid.

Any one know how to fix this?

---

### Post by SeijiSensei on 2016-01-15
Ordinary users can only write to /home/username and /tmp.  Everything else is owned by root, so Samba cannot access them except in read-only mode.

If you want to make changes  to other directories (risky and dangerous), use SSH to log into the machine and run commands with "sudo".  A decent SSH client for Windows is Putty: [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

---

### Post by bmarsh-bmarsh on 2016-01-18
I have done what this user wants to do for years.....    and it always worked like a charm.  However, my normal user login is also an admin, so that would give me some privs.    But since Samba was recently updated to 4.1.17 in  15.10, I have been unable to access ANYTHING.   Using win-7 I can access my wifes machine (15.04) in this manner (everything) but on my 15.10 machine I can't.  Win-7 sees everything on my machine (all the dirs) but it tells me I can't access anything.   Trying to solve the problem.

The section of my smb.conf that sets this up looks like:

[FONT=monospace][COLOR=#000000][root][/COLOR]
        path = /
        force group = users
        writable = yes
        public = yes
        force user = <myuserid> 
        guest ok = yes
[sysvol]
 path = /var/lib/samba/sysvol
  path = /
  read only = no

[netlogon]
  path = /var/lib/samba/sysvol/localdomain/scripts
  read only = no

Insert your own userid.[/FONT]

---

### Post by bab1 on 2016-01-18
> **bmarsh-bmarsh said:**
> I have done what this user wants to do for years.....    and it always worked like a charm. 

Earlier versions of Samba have had security issues.  Most of the problems have been solved with the introduction of Samba v4.
>  
However, my normal user login is also an admin, so that would give me some privs.    

There is only one administrative user and that is root.  Your user login only allows you to switch to root to do administrative tasks (via sudo).  Becase of the structure of Linux in general the mortal user (human) only needs to have rw access to their own home directory.  There is no reason to have rw access to the entire OS file system. 
> 
But since Samba was recently updated to 4.1.17 in  15.10, I have been unable to access ANYTHING.   Using win-7 I can access my wifes machine (15.04) in this manner (everything) but on my 15.10 machine I can't.  Win-7 sees everything on my machine (all the dirs) but it tells me I can't access anything.   Trying to solve the problem.
What problem?  Why would you need to "see" what you shouldn't access at all anyway.  Samba file sharing is for sharing user data across a local network.  That task is easily done. > 

The section of my smb.conf that sets this up looks like:

```

[root]
        path = /
        force group = users
        writable = yes
        public = yes
        force user = <myuserid> 
        guest ok = yes

```
This would not allow you access.  No parameter would be applied!  If the underlaying file system is owned by root (as most of it is) you will never be able to do anything.
```

[sysvol]
 path = /var/lib/samba/sysvol
  path = /
  read only = no

[netlogon]
  path = /var/lib/samba/sysvol/localdomain/scripts
  read only = no

```
Insert your own userid.
The defaults for this are for use with the Windows user admin module.  These have no direct bearing on file sharing

My advice is to share file systems you own and leave the rest alone.  If you have specific questions, start your own thread.  Hijacking others threads is poor form.  ;-)

---

