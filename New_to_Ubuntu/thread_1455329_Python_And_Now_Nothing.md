---
title: "Python And Now Nothing"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by amnite on 2010-04-15
Download python3 so i deleted python2, while p2 was being removed i went to the kicktchen and ubuntu restarted and said it was going to restart in low graphics mode(one session) i tried that and several other options to get ubuntu to start to no avail it just goes to the boot screen and sits there and does nothing... please help... btw lucid

---

### Post by amnite on 2010-04-15
ok in grub or the command prompt thing when i type linux i get this....
/usr/bin/python cant find '__main__.py' in '/usr/share/command not found,
this was after i was succesful in downloading the p2.6 from repository through grub. Still no luck with loading screen though. Something like has no drivers for anything on my computer and none of the options work...

---

### Post by 3rdalbum on 2010-04-15
> **amnite said:**
> Download python3 so i deleted python2

Bad idea. Pretty much most of your system depends on Python 2.6.  Python 3 is not a drop-in replacement. Didn't you smell a rat when the package manager told you that it was going to remove 200 packages?

If you can get to a command-line on your system, then you need to run:

```
sudo apt-get install ubuntu-desktop
```

which will reinstall Python 2.6 and many of the dependent packages that were also removed.

---

