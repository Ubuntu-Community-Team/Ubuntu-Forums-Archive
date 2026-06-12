---
title: "Increase ulimit -n"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by Sam Lars on 2009-08-04
I'm trying to increase the number of open files I can have for MySQL. I've searched a lot and found different suggestions.
I have the setting in my.cnf for MySQL at 4096, and I have the following in /etc/security/limits.conf
```
root hard nofile 4096
root soft nofile 4096

user hard nofile 4096
user soft nofile 4096

```
Supposedly after rebooting that's all there is to it?
I've rebooted many times and still ulimit -n returns 1024.

---

### Post by mike.gillan on 2009-08-19
I'd like to bump this thread - I'm having the same problem. I've had the following settings in my limits.conf since Jaunty launch:

```

*		hard	nofiles		4096
*		soft	nofiles		4096

```

But just recently I've started getting the "too many open files" error when working in Netbeans. Executing *ulimit -n* (and -n -H) tells me my open file limit is 1024:

```

mgillan@mandalore:~$ ulimit -n
1024

```

It seems /etc/security/limits.conf is not being applied. Anyone have any idea what's going on here?

TIA...

---

### Post by Sam Lars on 2009-08-19
Should it say "nofile" instead of "nofiles"?

---

