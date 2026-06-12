---
title: "package management error"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by noorez on 2009-11-24
I tried to uninstall a previous version of the adobe flash player and install a new one but it seems that the package management system has become corrupted

This error was reported by synaptic:

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

What do I do? Please help!

---

### Post by danking12 on 2009-11-24
In the terminal try:

```
sudo apt-get update
sudo apt-get purge adobe-flashplugin
sudo apt-get install adobe-flashplugin
```

If you receive an error copy and paste it in a reply.

---

### Post by noorez on 2009-11-24
Here is what I got:

```

noorez@noorez-laptop:~$ sudo apt-get purge adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

```

---

### Post by danking12 on 2009-11-24
Do you have the the extra repositories enabled? I"m not too sure which repository the flash plugin is located but check out the following section of the Ubuntu Guide, confirm the repositires are there and enabled and if not enable them and try again.

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Add_Extra_Ubuntu_Repositories]("http://ubuntuguide.org/wiki/Ubuntu:Karmic#Add_Extra_Ubuntu_Repositories")

---

### Post by noorez on 2009-11-25
All repositories are enabled....

If I do a 

apt-get install adobe-  (and hit the tab character from here), adobe-flashplayer shows up but I can't install it.

---

### Post by slakkie on 2009-11-25
[http://blog.opperschaap.net/2009/11/13/upgrade-flash-on-ubuntu-after-a-release-upgrade/](http://blog.opperschaap.net/2009/11/13/upgrade-flash-on-ubuntu-after-a-release-upgrade/)

---

### Post by Gazneth on 2009-11-25
Here is a copy of one of my older posts. noorez just run the bottom command and that will clear the reinstall loop you are stuck in. Be sure to plug in the correct package name.



```
sudo apt-get update
```

to update your package list.
Then

```
sudo apt-get autoclean
```

to clean up any partial packages.

```
sudo apt-get clean
```

to clean up the apt cache.

```
sudo apt-get autoremove
```

will clean up any unneeded dependencies.
If while doing this you can identify the broken package this code will very forcefully remove it.

```
sudo dpkg --remove --force-remove-reinstreq package name
```

Change package name to the real name of course.

---

### Post by Soul-Sing on 2009-11-25
> Please try to avoid running more than one update app at a time, e.g. terminal, Synaptic, update-manager GUI and so on.
Close all GUIs and only use terminal.
To avoid this error:
> E:The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it

try these cmds:
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin

sudo dpkg --configure -a
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install -f

sudo apt-get install flashplugin-installer
## Firefox should be closed and all other flash apps (e.g. swfdec, gnash) should be removed.

btw. to view which apps have been installed or removed, Synaptic has a history menu incl. a search inbox.

source: ubuntuanswers

---

