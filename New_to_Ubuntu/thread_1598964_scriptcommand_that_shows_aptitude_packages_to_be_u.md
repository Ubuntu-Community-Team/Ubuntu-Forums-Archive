---
title: "script/command that shows aptitude packages to be updated"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by eli_12345 on 2010-10-17
Hi,
im looking for a command or script that gives back a list of the packages that would be updated if an aptitude update would start...(it should not actually start the updates)
Cheers,
Eli

---

### Post by QLee on 2010-10-17
[QUOTE=eli_12345]Hi,
im looking for a command or script that gives back a list of the packages that would be updated if an aptitude update would start...(it should not actually start the updates)
Cheers,
Eli[/QUOTE]

There may be some confusion over terms. An aptitude update only updates your packages lists.

I think you really mean "upgrade" but I could be wrong about what you want to do. You can use the, -s, switch with the aptitude command to simulate. 


Here is an excerpt from the aptitude manual page (man aptitude):
       -s, --simulate
           In command-line mode, print the actions that would normally be
           performed, but don´t actually perform them. This does not require
           root privileges. In the visual interface, always open the cache in
           read-only mode regardless of whether you are root.

---

### Post by eli_12345 on 2010-10-17
Thanks...this is exactly what i was looking for :)

---

