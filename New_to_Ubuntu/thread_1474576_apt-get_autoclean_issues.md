---
title: "apt-get autoclean issues"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by BugBuster on 2010-05-06
This is the continuation of my previous thread below:

[http://ubuntuforums.org/showthread.php?t=1461187](http://ubuntuforums.org/showthread.php?t=1461187)

I still have the same issue. For example today I added xbmc-svn repo to the sources.list and did a apt-get update. Then I installed xbmc. All was fine until now. 

Then I tried "sudo apt-get -s autoclean" and this is what I get:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del nautilus 2.30.1-0ubuntu1 [1,273kB]
Del xbmc-bin 9.11+svn28042-lucid1 [15.7MB]
Del capplets-data 2.30.1-0ubuntu1 [321kB]
Del libqt3-mt 3.3.8-b-6ubuntu2 [3,523kB]
Del libgnome-window-settings1 2.30.1-0ubuntu1 [80.3kB]
Del xbmc-skin-confluence 9.11+svn28042-lucid1 [14.3MB]
Del xbmc-web 9.11+svn28042-lucid1 [146kB]
Del xbmc-data 9.11+svn28042-lucid1 [4,908kB]
Del xbmc 9.11+svn28042-lucid1 [32.0kB]
Del gnome-control-center 2.30.1-0ubuntu1 [413kB]
Del nautilus-data 2.30.1-0ubuntu1 [513kB]
Del libnautilus-extension1 2.30.1-0ubuntu1 [63.5kB]

```

As you can see apt-get wants to delete packages that are current, are installed and certainly valid. Also it deleted some updates packages that I installed this morning when I did "apt-get autoclean" accidentally. Same thing happened with pidgin,avidemux and many other packages!

Has anyone here noticed this. Please help as I want to have all the downloaded packages that are valid in the cache but at the same time delete outdated ones.

---

### Post by ankspo71 on 2010-05-06
"man apt-get" says...

>  autoclean
           Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           **APT::Clean-Installed** will prevent installed packages from being
           erased if it is set to off.
I never really explored this area of apt yet, so I don't know how to configure that. Maybe someone else here knows.

---

