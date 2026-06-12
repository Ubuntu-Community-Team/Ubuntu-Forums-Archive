---
title: "Deluge Error..."
date: 2009-04-22
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-04-22
I'm getting this error after trying to run deluge...

```
carl@mint-desktop ~ $ deluge
[ERROR   ] 21:06:35 ui:84 No module named gtkui.gtkui
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/deluge/ui/ui.py", line 65, in __init__
    from deluge.ui.gtkui.gtkui import GtkUI
ImportError: No module named gtkui.gtkui
[ERROR   ] 21:06:35 ui:85 There was an error whilst launching the request UI: gtk
[ERROR   ] 21:06:35 ui:86 Look at the traceback above for more information.

```


Linux Mint 6 amd64, based on intrepid:)

---

### Post by mhh91 on 2009-04-22
make sure you installed all the dependencies required to run the program,it seems like a gtk-related dependency is missing

---

### Post by kamitsukai on 2009-04-22
hmmm strange, reinstalled from synaptic and all works well now.. =]

---

### Post by recyclebin on 2009-06-01
It happened to me once, when I tried playing with the notification OSD from 9.04. It somehow got rid of the deluge package while retaining deluge-core and deluge-common. Installing deluge through Synaptic fixed it.

---

