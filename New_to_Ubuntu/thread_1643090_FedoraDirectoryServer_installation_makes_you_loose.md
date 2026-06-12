---
title: "FedoraDirectoryServer installation makes you loose PHP websites"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by alainr345 on 2010-12-11
I think it should be made much more plain clear that if you install Fedora Directory Server (389) on Ubuntu, you will instantly LOOSE any PHP web site running on the same server in the process!...

So the page [https://help.ubuntu.com/community/FedoraDirectoryServer](https://help.ubuntu.com/community/FedoraDirectoryServer)
should warn about that in 10-feet-high bold red letters.

In fact, it's not about that doc page I'm mostly complaining; the installer for that package should stop dead on it's track if it finds a combination of not-multi-threaded Apache AND PHP installed and ask the user to install a muti-threaded Apache AND PHP before going on!

After all, what idiot would want to install LDAP and loose its web sites in the process. Well, I'm the one it seems...

A very displeased user,
A. R.

---

