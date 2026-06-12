---
title: "Lock commands"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by VIV0411 on 2010-03-23
Is there any way we can lock commands(like rm)so as to prevent other users from executing it.

---

### Post by r-senior on 2010-03-23
You can take away execute permissions for group and world on /bin/rm but that could affect all sorts of things. Not all non-user processes run as root and might still need to delete files.

The Unix approach to security is to give a user free reign over their home directories and files they own. Correctly set up they can't do any damage other than to themselves. As long as they don't use sudo of course.

What's the problem you are trying to address?

---

### Post by jd65pl on 2010-03-23
Agreed you're able to stop mischief with effective permissioning rather than stopping users from running commands.

Another option would to be to alias rm to something else for example to move the target to another location.

---

