---
title: "usermod -G - becareful!"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by blur xc on 2009-08-14
I learned the hard way....

I'm reading the wiley linux command line and scripting bible- and they said that usermod -G "appends" a group to whatever user account you are modifying.  I found this to be false in Ubuntu, don't know if it's just different in other distro's, or a typo in the book.  It removes you from EVERY other group you belong to, except your default user group (modified by the -g option).  I managed to remove myself from the admin group and could no longer sudo anything.  Thank goodness for recovery mode...

The correct option is usermod -aG.  Lesson learned...

BM

---

### Post by LewRockwell on 2009-08-14
thank you for taking the time to post this

.

---

### Post by Joeb454 on 2009-08-14
This appears to be normal behaviour. From the mang page for usermod:

```
-a, --append
    Add the user to the supplemental group(s). Use only with -G option.

```

```
-G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
    A list of supplementary groups which the user is also a member of. Each group is separated from the next by a comma, with no intervening whitespace. The groups are subject to the same
    restrictions as the group given with the -g option. If the user is currently a member of a group which is not listed, the user will be removed from the group. This behaviour can be changed
    via the -a option, which appends the user to the current supplementary group list.

```

---

### Post by blur xc on 2009-08-14
> **Joeb454 said:**
> This appears to be normal behaviour. From the mang page for usermod:

```
-a, --append
    Add the user to the supplemental group(s). Use only with -G option.

``````
-G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
    A list of supplementary groups which the user is also a member of. Each group is separated from the next by a comma, with no intervening whitespace. The groups are subject to the same
    restrictions as the group given with the -g option. If the user is currently a member of a group which is not listed, the user will be removed from the group. This behaviour can be changed
    via the -a option, which appends the user to the current supplementary group list.

```

Oh yeah- I never doubted that it's not normal behavior.  My error was going by the book.  I discovered the error of my ways from reading the man pages.

From the Linux Command Line and Shell Scripting Bible, page 192.
> When you create a new group, there are no users assigned to it by default. The groupadd command
doesn’t provide an option for adding user accounts to the group. Instead, to add new users,
use the usermod command:
```
# /usr/sbin/usermod -G shared rich
# /usr/sbin/usermod -G shared test
# tail /etc/group
haldaemon:x:68:
xfs:x:43:
gdm:x:42:
rich:x:500:
mama:x:501:
katie:x:502:
jessica:x:503:
mysql:x:27:
test:x:504:
shared:x:505:rich, test
#
```The shared group now has two members, test and rich. The -G parameter in usermod _*appends*_
the new group to the list of groups for the user account.

Emphasis added by me...

BM

---

### Post by ubudog on 2009-08-14
Thanks for the advice! :)

---

### Post by Joeb454 on 2009-08-14
Ah ok, I must've misread it :) My mistake.

It may be worth emailing the publishers or something to see if they can get that amended. System breakage is never good.

---

### Post by blur xc on 2009-08-14
> **Joeb454 said:**
> Ah ok, I must've misread it :) My mistake.

It may be worth emailing the publishers or something to see if they can get that amended. System breakage is never good.

Adding myself back to the admin group isn't that big of a deal, but what I'm not sure of is if I'm supposed to be a member of any other system groups for whatever software permission reasons.  Maybe- I should back up my /etc/group file before farting around with stuff...

Does anyone use a script that backs up improtant user modifiable config files with a date code?  That would be cool- /etc/passwd, group, fstab, etc...  maybe that can be my first scripting project :D

BM

---

### Post by Dr Small on 2009-08-14
```
sudo adduser *user* *group*
```

---

