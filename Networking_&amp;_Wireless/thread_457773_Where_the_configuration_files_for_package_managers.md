---
title: "Where the configuration files for package managers are located ?"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by rksk16it on 2007-05-29
All of my package managers cannot reload or check the latest packages. The possible reason is that i'm unable to connect to **[http://in.archive.ubuntu.com](http://in.archive.ubuntu.com)** repository, please tell me where the config file resides, so that i can change from this default behaviour and lookup some other repository instead.

The GUI based program **System->Administration->Software Sources** is of no help as on changing the server it still attempts to reload the list from **[http://in.archive.ubuntu.com](http://in.archive.ubuntu.com)**, and then cries out loud that there are network problems. If i can locate the config file containing the address **[http://in.archive.ubuntu.com](http://in.archive.ubuntu.com)**, i can simply change it to point somewhere else.

Thanks in advance for help :)

---

### Post by tkjacobsen on 2007-05-29
/etc/apt/sources.list is maybe what you are looking for?

---

### Post by rksk16it on 2007-05-29
Thanks for the location :), but....

Even if i change the repository, the synaptic-manager ( or for that matter any GUI based package manager) are still unable to download, whereas using **Firefox** i **can** download all those files...:-?

What is such a thing that Firefox can do but all those applications can't....:-?

Thanks again if anyone can help :)

---

