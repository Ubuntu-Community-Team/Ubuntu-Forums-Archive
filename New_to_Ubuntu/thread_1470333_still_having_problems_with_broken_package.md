---
title: "still having problems with broken package"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by richie3418 on 2010-05-02
I am still having a problem with a broken package. I can't do anything to it, it is the Adobe Flash plugin. There is no installer after the upgrade I made yesterday. I tried to uninstall the plug in and install the installer I get this message every time: E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal. I tried what someone mentioned yesterday about (fix broken packages) and that didn't work. 
Is there a way to take all the fire fox packages of the reinstall them or some way to fix this mess?

---

### Post by sandyd on 2010-05-02
> **richie3418 said:**
> I am still having a problem with a broken package. I can't do anything to it, it is the Adobe Flash plugin. There is no installer after the upgrade I made yesterday. I tried to uninstall the plug in and install the installer I get this message every time: E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal. I tried what someone mentioned yesterday about (fix broken packages) and that didn't work. 
Is there a way to take all the fire fox packages of the reinstall them or some way to fix this mess?
see mi sig.

---

### Post by sandyd on 2010-05-02
> **richie3418 said:**
> I am still having a problem with a broken package. I can't do anything to it, it is the Adobe Flash plugin. There is no installer after the upgrade I made yesterday. I tried to uninstall the plug in and install the installer I get this message every time: E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal. I tried what someone mentioned yesterday about (fix broken packages) and that didn't work. 
Is there a way to take all the fire fox packages of the reinstall them or some way to fix this mess?
or```

sudo rm /var/lib/dpkg/info/flashplugin-nonfree.post*
sudo rm /var/lib/dpkg/info/flashplugin-nonfree.pre*
sudo dpkg --purge --force all flashplugin-nonfree

```

---

