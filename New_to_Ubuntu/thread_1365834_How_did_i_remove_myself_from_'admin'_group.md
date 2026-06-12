---
title: "How did i remove myself from 'admin' group ?"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by iMisspell on 2009-12-27
While configuring Subversion i wanted to add my current UserName to the subversion group and did the following.

```
sudo usermod -G subversion MyUserName
```

Just now i went to sudo something and could not, check what groups i belonged to and seen i was no longer in the 'admin' group, only groups i now belong to are 'UserName' and 'Subversion'.

So from root i ran ```
usermod -a -G subversion MyUserName
``` and now im both 'admin' and 'Subversion'.

When using...
```
sudo usermod -G [group] MyUserName
```
It remove you from all groups and only adds you to the group name in the command ?

Everything is ok now, but i'd like to know the cause of this.

[edit]
This was done though ssh to ubuntu 8.04 server, from ubuntu 9.04 desktop
_

---

### Post by bodhi.zazen on 2009-12-27
see man usermod =)

[http://linux.die.net/man/8/usermod](http://linux.die.net/man/8/usermod)

> 
**-g**, **--gid** *GROUP* The group name or number of the user's new initial login group. The group name must exist. A group number must refer to an already existing group. The default group number is 1. 

**-G**, **--groups** *GROUP1*[*,GROUP2,...*[*,GROUPN*]]] A list of supplementary groups which the user is also a member of. Each group is separated from the next by a comma, with no intervening whitespace. The groups are subject to the same restrictions as the group given with the **-g** option. If the user is currently a member of a group which is not listed, the user will be removed from the group. This behaviour can be changed via **-a** option, which appends user to the current supplementary group list.

---

### Post by sisco311 on 2009-12-27
```
man usermod | less +/-G,
```

EDIT: never mind, i'm too slow. :)

EDIT2:

You could use gpasswd or adduser (on a debian based system) to add a user to a group:
```
adduser user group
gpasswd -a user group
```

---

### Post by DaithiF on 2009-12-27
> **iMisspell said:**
> 
```
sudo usermod -G [group] MyUserName
```It remove you from all groups and only adds you to the group name in the command ?

Everything is ok now, but i'd like to know the cause of this.

This is the expected behaviour, as the man page for usermod says:
**-G**, **--groups** *GROUP1*[*,GROUP2,...*[*,GROUPN*]]] A list of supplementary groups which the user is also a member of. Each group is separated from the next by a comma, with no intervening whitespace. The groups are subject to the same restrictions as the group given with the **-g** option. If the user is currently a member of a group which is not listed, the user will be removed from the group. This behaviour can be changed via **-a** option, which appends user to the current supplementary group list.

---

### Post by iMisspell on 2009-12-27
Thanks all... i get the point... man page... man page... read... read... :P

Been a long time Windows User and the help files from there... well, im sure there's enough windows bashing here.

I completely forget about man pages.


Thanks for the reminder and insight.


_

---

### Post by bodhi.zazen on 2009-12-27
> **iMisspell said:**
> Thanks all... i get the point... man page... man page... read... read... :P

Learning to read the man pages is intimidating at first, but an invaluable skill.

If you prefer, they are available on line as well ;)

---

### Post by iMisspell on 2009-12-28
yea - Im just not used to having help files which really help ;)
Normaly i would tinker with "this and that" and search the net... gonna take alittle while to break bad habbits :)

---

