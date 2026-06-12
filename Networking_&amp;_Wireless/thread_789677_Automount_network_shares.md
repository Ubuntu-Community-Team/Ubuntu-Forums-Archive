---
title: "Automount network shares?"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by WeeManDan on 2008-05-10
Hi all,

I just wondered, is there a way to automount network ssh shares on logon, similar to automounting an NTFS partition?

Thanks,

Dan

---

### Post by nixscripter on 2008-05-11
Depending on what permissions you want them to have on the local machine, you can always use /etc/fstab for mounting at system startup.

If you, for example:```
mount -t type -o options remote /my/mount/dir
```

You can probably put in a simple fstab entry like this:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
remote          /my/mount/dir   type    options         0       0

```

If you want it at log in (i.e. your user only), I would suggest just writing a shell script to mount it (if you need to have user input, run it with **gnome-terminal -e "script"**) and put it in the login items under System->Preferences->Sessions.

---

