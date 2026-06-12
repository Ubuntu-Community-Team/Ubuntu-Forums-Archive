---
title: "Firefox safe mod ?"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by yaacovk on 2009-11-17
Hello.
Ubunto 9.10
yesterday i had a problem with my Firefox (ver 3.5.5)
the top screen was frozen, it was impossible to type any address
or go to the bar menu to change something.
in addition, before few days i installed a tool bar of AOL music.
i tried to open the Firefox with: ~firefox %u.
the browser came up with no site but it's doesn't help.
i tried to get in to remove the tool bar of the AOL music but i can't
there is a way to start that browser as a safe mod?

Thanks in advance.

Yaacov.

---

### Post by hovzio on 2009-11-17
hi, if all else fails you can reset your firefox profile with 
```

rm -rf .mozilla
```

make sure to backup your bookmarks first. After doing this firefox will be "reset", I think the toolbar should be gone. How did you install this aol toolbar? If you installed it through firefox it will be removed, as well as all your firefox extensions. happy computing ;)

---

### Post by philinux on 2009-11-17
> **yaacovk said:**
> Hello.
Ubunto 9.10
yesterday i had a problem with my Firefox (ver 3.5.5)
the top screen was frozen, it was impossible to type any address
or go to the bar menu to change something.
in addition, before few days i installed a tool bar of AOL music.
i tried to open the Firefox with: ~firefox %u.
the browser came up with no site but it's doesn't help.
i tried to get in to remove the tool bar of the AOL music but i can't
there is a way to start that browser as a safe mod?

Thanks in advance.

Yaacov.
Open a terminal.

```
firefox -safe-mode
```

---

