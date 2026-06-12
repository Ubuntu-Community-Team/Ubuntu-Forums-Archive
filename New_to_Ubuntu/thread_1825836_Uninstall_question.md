---
title: "Uninstall question"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by Depray on 2011-08-15
Hey guys,

So I am installing ubuntu server on a mediaserver. I was having a little bit of an issue setting up a few things so I figured I would just ran ```
apt-get install ubuntu-desktop
```
thinking that I could just remove the package and didn't really stop to thing that it also install a bunch of the dependencies. So now the time has come I'm done configuring everything and now I'm trying to remove the GUI and scale back to the ubuntu server. issue is now that everything else is loaded the a bunch of stuff I don't want. Does anyone know of a way how the keep the settings of everything but scaling the system back to a pre-desktop server defaults? I would even be perfectly content with not having it loading any additional process but I'm not sure if just removing the ubuntu-desktop would be enough to do that.

Best Regards,
James

---

### Post by 3rdalbum on 2011-08-15
Removing 'ubuntu-desktop' itself won't remove the dependencies that were installed, but it will mark those other packages as "orphans".

```
sudo apt-get remove ubuntu-desktop
sudo apt-get autoremove
```

will remove ubuntu-desktop, and then remove the orphans (all the packages that were installed as dependencies of ubuntu-desktop).

---

