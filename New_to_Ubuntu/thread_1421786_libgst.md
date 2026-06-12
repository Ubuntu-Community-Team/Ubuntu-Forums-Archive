---
title: "libgst"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by tomwagner13 on 2010-03-04
hey so i am not able to launch any of my music players or ubuntu software center.  It is because my libgst files are deleted as the following shows.  Anyone know how to fix this?

mucho gracias

Traceback (most recent call last):
  File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 43, in <module>
    from view.installedpane import InstalledPane
  File "/usr/share/software-center/softwarecenter/view/installedpane.py", line 36, in <module>
    from softwarepane import SoftwarePane, wait_for_apt_cache_ready
  File "/usr/share/software-center/softwarecenter/view/softwarepane.py", line 38, in <module>
    from appdetailsview import AppDetailsView
  File "/usr/share/software-center/softwarecenter/view/appdetailsview.py", line 52, in <module>
    from widgets.wkwidget import WebkitWidget
  File "/usr/share/software-center/softwarecenter/view/widgets/wkwidget.py", line 27, in <module>
    import webkit
ImportError: libgstvideo-0.10.so.0: cannot open shared object file: No such file or directory

---

### Post by lykwydchykyn on 2010-03-04
Looks like the file in question is part of the libgstreamer-plugins-base0.10-0 package.

Open a terminal window and try the following:
```

sudo apt-get install libgstreamer-plugins-base0.10-0

```

See if that will fix it.

---

### Post by tomwagner13 on 2010-03-04
great success! i used the package manager to reinstall them, the terminal couldnt find it
thank you much-

---

