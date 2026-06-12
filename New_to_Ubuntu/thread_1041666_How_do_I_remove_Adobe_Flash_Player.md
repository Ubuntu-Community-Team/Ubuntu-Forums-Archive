---
title: "How do I remove Adobe Flash Player?"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by BertP on 2009-01-16
I just installed Ubuntu 8.04  and installed Adobe flash player plugin 10 
from a link at youtube

result: Adobe player is installed  but it still doesn't work in Firefox!

but now that it is installed, any attempts to install other flashes players doesn't work


so I searched and found the install file "/tmp/install_flash_player_10_linux.deb"

double clicking on this file gives me several tabs of information and it even includes a "reinstall" button..... does anyone know how to uninstall the whole package ??? or must I track down every file it placed and remove them manually?

---

### Post by bwang on 2009-01-16
Open Synaptic Package Manager, search for flash player, and uninstall the package.

---

### Post by taurus on 2009-01-16
You can uninstall that package from a terminal.

Applications -> Accessories -> Terminal
```
sudo dpkg -r install_flash_player_10_linux
```

---

### Post by BertP on 2009-01-16
Thanks it works but you have to use this package name ->  

adobe-flashplugin

---

