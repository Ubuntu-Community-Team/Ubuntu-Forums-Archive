---
title: "Remove upstream gstreamer plugins"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by deancasino on 2010-07-02
Hey guys I need to know how to remove the upstream gstreamer plugins and return to the maintainers version.

Some command to purge?

---

### Post by ajgreeny on 2010-07-02
I presume you must have enabled repos for that (backports or proposed?) and if so just disable them, refresh the repos ```
sudo apt-get update
```then remove the packages, and reinstall them, or if using synaptic you can choose "force version" from the package menu.

---

