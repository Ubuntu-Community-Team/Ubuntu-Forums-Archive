---
title: "Error message update manager"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by rootessa on 2011-04-06
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ramroberto/java/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/ferramroberto-java-maverick.list'


I'm SO excited to have yet another new problem that I almost can't stand it! I tried to run update manager for the first time since updating to 10.10 and this is the message I got. I Anybody? I'm thinking I have a really expensive doorstop at this point. Thanks! ](*,)

---

### Post by wolfen69 on 2011-04-06
Deleting line 2 in that file would probably fix it, since it is not known anyway. My /etc/apt/sources.list.d is empty.

---

