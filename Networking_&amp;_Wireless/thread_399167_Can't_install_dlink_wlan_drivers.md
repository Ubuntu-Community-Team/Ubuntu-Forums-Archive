---
title: "Can't install dlink wlan drivers"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by tcroc26 on 2007-04-02
I have a Dlink DWL-G520 wireless card.  I downloaded and tried to install the package: 

linux-restricted-modules-2.6.10-5-386_2.6.10.5-1gb_i386.deb

...however when I tried to install this package this is the error message that I received:

Error:  dependency is not satisfiable:  linux-image-2.6.10-5-386

Any ideas as to why i'm getting this error messages and how can I correct this?  I'm fairly new to operating linux, a definite novice user.  Thanks for any help in advance!

---

### Post by Floppyjoe on 2007-04-02
You may need to install linux-headers for your kernel version as well as build-essential.

You can use the Ubuntu install cd as a repository by clicking on System/Administration/Synaptic Package Manager.
Then click Edit/Add CDrom and follow the instructions.
Then click Reload.
Then search for linux-headers and build-essential.
You can find your kernel version with the command:
```
uname -r
```
from the terminal. To open a terminal Click on Applications/Accessories/Terminal.

---

