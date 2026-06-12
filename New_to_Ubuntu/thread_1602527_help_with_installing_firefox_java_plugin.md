---
title: "help with installing firefox java plugin"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by jarongg on 2010-10-21
running ubuntu lucid. i have the newest version of java installed but i need help installing the firefox plugin or otherwise it's sort of worthless to me. i was hoping i could get the most basic walkthrough on how to do this. i don mind command line if it's straight forward, but last time i tried to compile this it was an utter failure. they should just make a .deb package for this. thanks guys!!:)

---

### Post by sikander3786 on 2010-10-21
Simple instructions here.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by jarongg on 2010-10-21
sorry, but i don't find that page helpful at all. i have the icedtea plugin installed, but other than that that page gives no info on how to install the firefox java plugin.

---

### Post by lykeion on 2010-10-21
Quoted from the page mentioned:
"For applet support in the browser, install sun-java6-plugin [...] see the instructions in the Lucid release notes."

Lucid release notes (under Sun Java moved to the Partner repository):
"[Y]ou can install sun-java6 packages from the Canonical Partner Repository. You can configure your system to use this repository via command-line":
```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
sudo apt-get update
```

---

### Post by gandaran on 2010-10-21
> **jarongg said:**
> sorry, but i don't find that page helpful at all. i have the icedtea plugin installed, but other than that that page gives no info on how to install the firefox java plugin.
the icedtea plugin is the java firefox plugin for openjdk-java, if you don't want to use openjdk-java remove all the openjdk packages or just the icedtea plugin if you have any openjdk dependent applications.
to install sun-java you have to enable the archive.canonical partner repository in software sources and update the package list, after doing this you will find the sun-java packages in synaptic or software center ready to install.
package list update command
```
sudo apt-get update
``` 
sun-java install command
```
sudo apt-get install sun-java6-plugin
```

---

### Post by wojox on 2010-10-21
```
sudo apt-get update; sudo apt-get install ubuntu-restricted-extras
```

Java works great here.

---

### Post by lykeion on 2010-10-21
ubuntu-restricted-extras does not include sun-java6-plugin, only icedtea6-plugin and a lot of other unrelated packages:
[http://packages.ubuntu.com/lucid/ubuntu-restricted-extras](http://packages.ubuntu.com/lucid/ubuntu-restricted-extras)

---

