---
title: "Firefox not reponding"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by singhs on 2009-08-09
I keep getting this message eventhough I quit Firefox using File-Quit command.

Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.

Please help

---

### Post by Zill on 2009-08-09
Open a terminal (menu Applications, Accessories, Terminal) then enter the following code:
```
killall firefox-bin
```

---

### Post by swong on 2009-08-09
If you were viewing websites with Flash content prior to quitting Firefox, maybe the plugin npviewer.bin has not finished shutting down.

You can try to check if that process is still running and kill it (I just use System Monitor because I can't always remember the process names).

---

