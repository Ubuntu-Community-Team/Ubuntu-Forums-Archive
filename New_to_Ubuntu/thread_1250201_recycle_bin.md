---
title: "recycle bin?"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by adsy mac on 2009-08-26
how do i access my recycle bin? when i first used to delete items, it would show a little bin logo in the bottom right hand side of the screen but its not doing that anymore.

---

### Post by drs305 on 2009-08-26
You can try to turn on the Trash icon for the Desktop by running this command:
```
gconftool-2 --type bool --set /apps/nautilus/desktop/trash_icon_visible "true"
```

If you can't get the icon back on your Desktop, you can make a shortcut on the panel by Right Click, Add to Panel, Trash.

You can access your trash with the following command. Use SHIFT-DEL to delete the **Trash** folder, which empties the trash and removes the subfolders until something else is deleted.
```
nautilus $HOME/.local/share
```

Added: Here is a link to a post I wrote a while back on the 'Trash' system:
[http://http://ubuntuforums.org/showthread.php?t=898573]("http://http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by adsy mac on 2009-08-26
> **drs305 said:**
> You can try to turn on the Trash icon for the Desktop by running this command:
```
gconftool-2 --type bool --set /apps/nautilus/desktop/trash_icon_visible "true"
```If you can't get the icon back on your Desktop, you can make a shortcut on the panel by Right Click, Add to Panel, Trash.

thanks a lot drs305, that code worked just fine :P
much appreciated.

---

