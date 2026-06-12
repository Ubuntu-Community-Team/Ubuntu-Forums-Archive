---
title: "software uninstall"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by wirate on 2009-08-21
When I install a package from the repos for the first time, it does some downloading. I remove the package, reinstall it and this time it doesn't download anything. This means that the installation files were never removed. Why?

---

### Post by iEthan on 2009-08-21
That's because Ubuntu archives installation files. Don't ask me why. Get rid of them with the following bash command:

```
sudo apt-get purge [program name]
```

---

### Post by Penguin Guy on 2009-08-21
> **iEthan said:**
> That's because Ubuntu archives installation files. Don't ask me why. Get rid of them with the following bash command:

```
sudo apt-get purge [program name]
```
It's because sometimes there might be an error with a program which causes it to stop working (as I assume is the case with the original poster). In this case the user can uninstall and reinstall the package without access to the internet. So if you don't think you'll ever want a package again (or you don't mind re-downloading it from the internet) use [COLOR="Green"]sudo apt-get purge[/COLOR] as iEthan suggested.

---

### Post by xPr0star on 2009-08-21
Also you should try to run autoremove. Lets say im uninstalling esperanza we would do

```
sudo apt-get purge esperanza
sudo apt-get autoremove esperanza
```

Ubuntu will also leave traces in the /usr/share/app-install folder as well as /usr/share/

---

### Post by ajgreeny on 2009-08-21
```
sudo apt-get clean
``` will also remove all packages from the cache (/var/cache/apt/archives) and clean up a lot of space, if you are short of it.
```
sudo apt-get autoclean
```will remove all un-needed packages.

Have a look at [http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html) for more details of all available ways od dealing with this.

---

