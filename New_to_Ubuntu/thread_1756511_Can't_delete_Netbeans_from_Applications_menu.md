---
title: "Can't delete Netbeans from Applications menu"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by faint545 on 2011-05-12
Hi guys, I've been using Ubuntu for a while now and I really do love it.

I recently uninstalled Netbeans from my system using the uninstall script that came with Netbeans. However, the program item is still under Applications > Programming > Netbeans IDE 7.0.

For some reason every time I try to delete it, it doesn't work... I also searched my system for anything relating to Netbeans and deleted those files (except for icons).

Any ideas?

---

### Post by frankbooth on 2011-05-12
Launch the terminal and type:
```

cd /usr/share/applications/
ls

```
Do you have 'netbeans.desktop' in there?

If yes:
```
rm netbeans.desktop
```

Else, *shrug*

---

### Post by faint545 on 2011-05-12
Nope. It's not in there.

[EDIT]: Fixed problem. I forgot to restart when I had deleted all files pertaining to Netbeans. After restart, it's gone.

---

