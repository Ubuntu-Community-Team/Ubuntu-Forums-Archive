---
title: "Is there a way to &quot;countdown to the next fsck at boot&quot;?"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by diablo75 on 2010-08-02
File system checks drag me down some days when I wanna get on the computer and am split between canceling a full scan or letting it run so I don't have to worry about it next time.  If I knew in advanced when a scan was going to take place, I'd plan for it... probably by restarting the computer before I walk away to go eat lunch or something.  I was wondering if there might be a way to implement a little countdown or even be able to open a file and check to see how many more boots are left before the automatic file system check.

---

### Post by sisco311 on 2010-08-02
A full filesystem check is performed after X mounts (by default, ~20 for the / partition and ~30 for others) or after Y days (by default, 6 months) since the last full check.

You can use **tune2fs -l** to list the current and maximim mount count and the next check date:
```
sudo tune2fs -l /dev/**sdXY** | grep -i -e "mount count" -e "check"
```

---

### Post by oldos2er on 2010-08-02
```
sudo apt-get install showfsck
```

---

### Post by JustinR on 2010-08-02
> **sisco311 said:**
> A full filesystem check is performed after X mounts (by default, ~20 for the / partition and ~30 for others) or after Y days (by default, 6 months) since the last full check.

You can use **tune2fs -l** to list the current and maximim mount count and the next check date:
```
sudo tune2fs -l /dev/**sdXY** 2> /dev/null | grep -i -e "mount count" -e "check"
```

+1

But I would remove the '2> /dev/null' as it gives permission errors even if you're using sudo. The command works fine without it.

---

### Post by sisco311 on 2010-08-02
> **JustinR said:**
> +1

But I would remove the '2> /dev/null' as it gives permission errors even if you're using sudo. The command works fine without it.

Oops... fixed! sudo is needed only if your user has no read permissions for /dev/sdXY. I'm too lazy to boot in Ubuntu to check out what permissions & ownership are assigned for /dev/sdXY. :)

@oldos2er, I didn't know about showfsck. It's a nice app, but it doesn't show the *next check date*, which may be useful if computer is not (re)booted too often.

---

