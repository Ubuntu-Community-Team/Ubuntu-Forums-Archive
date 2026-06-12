---
title: "Compiz freewins plug-in"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by lonewolf1222 on 2009-01-26
How do I install the Compiz freewins plug-in? I read on here that you can get it from the compiz git tree. What is that? Can someone tell me step by step?

---

### Post by zephyrcat on 2009-01-26
Information on installing Compiz Fusion plugins can be found here:

[http://wiki.compiz-fusion.org/Install/PluginsFromGit](http://wiki.compiz-fusion.org/Install/PluginsFromGit)

For your specific case:

1. Install git-cvs (either go to System->Administration->Synaptic Package Manager and search for "git-cvs" or type in to a terminal "sudo apt-get install git-cvs).

2. Type these commands in the terminal (Applications->Accessories->Terminal):
```
git clone	git://anongit.compiz-fusion.org/users/warlock/freewins
cd ~/.compiz/plugins
make
make install
git pull origin
make clean
make
make install
```
Basically, that copies the files down from the server (line 1), navigates you to the download directory (line 2), compiles the plugin (lines 3-4), and updates it (lines 5-8).

I have not tested this myself, but it should work. Let me know if you have issues.

---

