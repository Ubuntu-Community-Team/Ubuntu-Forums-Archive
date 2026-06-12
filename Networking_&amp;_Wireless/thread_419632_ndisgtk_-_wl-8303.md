---
title: "ndisgtk - wl-8303"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by tompot on 2007-04-23
I've finally installed ndiswrapper with ndisgtk. Network card was detected but after reboot I couldn't run ndisgtk. In terminal I get such error
```

(ndisgtk:5157): libglade-WARNING **: Could not load support for `gnome': libgnome.so: cannot open shared object file: No such file or directory
Traceback (most recent call last):
  File "/usr/bin/ndisgtk", line 309, in <module>
    NdisGTK()
  File "/usr/bin/ndisgtk", line 111, in __init__
    self.setup_driver_list()
  File "/usr/bin/ndisgtk", line 140, in setup_driver_list
    self.get_driver_list()
  File "/usr/bin/ndisgtk", line 168, in get_driver_list
    driver_name = p.search(line).group()[:-1]   # strip trailing space
AttributeError: 'NoneType' object has no attribute 'group'

```

Does anyone know solution?:confused:

---

### Post by SuperD2000 on 2007-07-04
I am also getting the same error.  Has anyone found out what was wrong with this?

---

