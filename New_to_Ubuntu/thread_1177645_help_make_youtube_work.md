---
title: "help make youtube work"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by silvernitrate on 2009-06-03
can someone help me get youtube to work  it tells me i need java or flash i don't know if i need the runtime or the web start  java from the add remove section or if i should bother with flash i have the new ubuntu and like it a lot i just want everything to be perfect

---

### Post by Donnut on 2009-06-03
You will need to install flash for firefox to work with youtube, you can go to adobe's website, download flash for ubuntu, and just double-click it to install it.

---

### Post by balloooza on 2009-06-03
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb)
tada, and BTW, it says it wants JAVASCRIPT, this is different from java, You probobly dont even need java (I never seem to use it!)

---

### Post by Tibuda on 2009-06-03
Or install the [flashplugin-nonfree]("apt:flashplugin-nonfree") package from Ubuntu package manager.

---

### Post by LewRockwell on 2009-06-03
> **danielrmt said:**
> Or install the [flashplugin-nonfree]("apt:flashplugin-nonfree") package from Ubuntu package manager.

seconded the package manager

---

### Post by Donnut on 2009-06-03
Oh wait, that's the easy approach guys!  I was thinking the windows way!
Why do the web searching/downloading when synaptic will do it all for you!

---

### Post by Adam N on 2009-06-03
I tried to download flash from the website but it did not work for me, i downloaded all of the java packages and it has worked for me. Adam

---

### Post by UbuntuNerd on 2009-06-03
why don't you just type this in a terminal to get flash:
```
sudo apt-get install flashplugin-nonfree
```

java plugin: 
```
sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin
```

---

