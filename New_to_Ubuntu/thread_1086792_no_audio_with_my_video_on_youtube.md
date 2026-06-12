---
title: "no audio with my video on youtube"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by firewarrior on 2009-03-04
Ok....so here's the deal. I have a problem with my flash player. For some reason i can not get it to install correctly. I've done the following in my terminal

- sudo apt-get install flashplugin-nonfree and I get the following: Download done.
md5sum mismatch install_flash_player_10_linux.tar.gz
The Flash plugin is NOT installed.

I try to do an update as well and still nothing happens. If anyone out there could shine some light on this for me that would be very much helpful.

---

### Post by LowSky on 2009-03-04
32 or 64bit?

have you tried this to install it?

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by firewarrior on 2009-03-04
I'm running a 64 bit and I tried that line of code and still nothing happens.

---

### Post by gandaran on 2009-03-04
it's better you install the 64-bits adobe beta flash, get it [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz") to install extract the package and move the libflashplayer.so file to /home/'user'/.mozilla/plugins (make the plugins folder) or if you have more than one user account place it in /usr/lib/mozilla/plugins.
don't forget to remove the broken flashplugin-nonfree package, the reason it didn't install flash is because the package is outdated, to get the new package list you must update synaptic (sudo apt-get update or click the reload button in synaptic)

---

