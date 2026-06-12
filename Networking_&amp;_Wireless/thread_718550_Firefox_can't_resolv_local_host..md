---
title: "Firefox can't resolv local host."
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by Joe_Bishop on 2008-03-08
1. I was forced to add current user (master) to all groups with
```
for group `cat /etc/group | awk -F: '{print $1}'`; do addgroup master $group; done
```
2. After that firefox stop on "looking up ..." while using local hosts, although there is no problem for external hosts
3. nslookup and host work fine.

---

### Post by Eiríkr on 2008-03-09
> 1. I was forced to add current user (master) to all groups with
```
for group `cat /etc/group | awk -F: '{print $1}'`; do addgroup master $group; done
```

To borrow a phrase, "I do not think that means what you think it means."  From the help notes for addgroup:
```
adduser --group [--gid ID] GROUP
addgroup [--gid ID] GROUP
   Add a user group

addgroup --system [--gid ID] GROUP
   Add a system group

adduser USER GROUP
   Add an existing user to an existing group
```

I'm not very good with scripting, but I couldn't get this to work; I keep getting an error:
```
-bash: syntax error near unexpected token ``cat /etc/group | awk -F: '{print $1}'`'
```

Anyway -- from the command's own help description, it sounds like so what your command would do is *not* to add user "master" to all groups, but rather to add a group called "master".  It looks like you'd need to use the alternate syntax [font=courier]adduser USER GROUP[/font] for your [font=courier]do[/font] section.  

Cheers,

Eiríkr

---

### Post by Joe_Bishop on 2008-03-09
adduser, not addgroup, exactly.
I solved the problem, just commented the "alias net-pf-10 ipv6" in the /etc/modprobe.d/aliases

---

### Post by Eiríkr on 2008-03-09
Glad to hear you resolved the issue. :)   If that does it for you then, please also mark this thread as SOLVED in the Thread Tools dropdown at the top of the page to let other Forum browsers know this thread is all set.  

Cheers,

Eiríkr

---

