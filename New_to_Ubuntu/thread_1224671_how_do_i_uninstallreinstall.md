---
title: "how do i uninstall/reinstall?"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by Darkoblivion2 on 2009-07-27
i need to know the terminal cmd to uninstall and then reinstall my flash plugins...

my computer is hard freezing sometimes when i view web pages with flash...

any and all help is appreciated!

---

### Post by fooman on 2009-07-27
open a terminal (applications > accessories > terminal) and type or copy/paste the following commands, one at a time...pressing enter after each one:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

from here:
[http://ubuntuforums.org/showthread.php?t=1218058&highlight=flash+gnash+swfdec&page=3](http://ubuntuforums.org/showthread.php?t=1218058&highlight=flash+gnash+swfdec&page=3)

hope that helps.

---

### Post by wojox on 2009-07-27
lovinxlinux did a nice tutorial on this:

[http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004)

---

### Post by Darkoblivion2 on 2009-07-27
thank u kindly!

---

