---
title: "What is the configuration folder and files for Gnome panels?"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by legolas_w on 2009-05-10
Hi
I think gnome panels for ubuntu 9.04 is not compatible with gnome panels for ubuntu 8.10 therefore the panels are not functioning correctly.

If you know what is path to gnome panel configuration files, I might be able to delete the old files and let ubuntu creates new ones again.


thanks

---

### Post by Didius Falco on 2009-05-10
I wouldn't delete them, I'd just rename the folder and see how it work for you. According to this bug report, renaming the ~/.gconf folder fixed it for several people.

Here is a link to that bug report:

[https://bugs.edge.launchpad.net/ubuntu/+bug/371585](https://bugs.edge.launchpad.net/ubuntu/+bug/371585)

I hope it helps,

Regards,

Didius

---

### Post by legolas_w on 2009-05-10
Thank you for the link. I tried it but it does not resolve the problem.
My only problems are:

- Can not add anythign to panels or remove anything from panels
- Can not move panel.

If you come across a solution, please let me know.


Thanks.

---

### Post by Didius Falco on 2009-05-10
Sorry that didn't help. Have you tried creating a new panel and trying to add some things to that? If that works, you could simply recreate your old panels and then delete the old ones...

Probably a long shot, but worth a try.

Regards,

Didius

---

### Post by legolas_w on 2009-05-12
> **legolas_w said:**
> Thank you for the link. I tried it but it does not resolve the problem.
My only problems are:

- Can not add anythign to panels or remove anything from panels
- Can not move panel.

If you come across a solution, please let me know.


Thanks.

Any idea or solution?

Thanks.

---

### Post by adrianx on 2009-05-12
It sounds like your panels could be locked down.

Try this:
```
gconftool-2 --type bool --set /apps/panel/global/locked_down "false"
```

---

### Post by legolas_w on 2009-05-12
> **adrianx said:**
> It sounds like your panels could be locked down.

Try this:
```
gconftool-2 --type bool --set /apps/panel/global/locked_down "false"
```

Thank you, it resolved the problem for me.

---

