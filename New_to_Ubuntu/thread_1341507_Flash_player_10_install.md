---
title: "Flash player 10 install"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by The Eight-Bit Link on 2009-11-29
I cannot use the rpm, the tarball (when extracted0 leaves me with a single file labeled '.', and the .deb file doesn't work. I would like some help (being a total noob and all...)

---

### Post by BenAshton24 on 2009-11-29
[Click Me :)]("apt:flashplugin-nonfree")

Or just run the following in terminal...
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by SunnyRabbiera on 2009-11-29
the .deb usually works, but are you using 64bit?

---

### Post by The Eight-Bit Link on 2009-11-29
32- bit... or less.. This laptop is frightfully outdated... 
The link comes up with an error saying it could not find the package.
The deb when it checks teh package says
Error: Dependency is not satisfiable: libnspr4-dev

---

### Post by jrrader on 2009-11-29
Install libnspr4-dev and try again.

---

### Post by SunnyRabbiera on 2009-11-29
Odd it is not installing the dependency though, usually gdebi is good with that sort of thing

---

### Post by The Eight-Bit Link on 2009-11-29
okay... how do I install the libnspr4-dev file? (This is my first actual day of usage from windows)

---

### Post by sandyd on 2009-11-29
> **jrrader said:**
> Install libnspr4-dev and try again.
its a current known problem in karmic. libnspr4 was renamed in karmic, and it seems that someone in mainstream hasnt updated the dependencies yet.......

in other words.. just copy and paste....
```

wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
tar xvfz install_flash_player_10_linux.tar.gz
sudo mv *.so /usr/lib/firefox/plugins/
rm install_flash_player_10_linux.tar.gz

```

---

### Post by SunnyRabbiera on 2009-11-29
> **carlee said:**
> its a current known problem in karmic. libnspr4 was renamed in karmic, and adobe seems to be lagging behind.....

in other words.. just copy and paste....
```

wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
tar xvfz install_flash_player_10_linux,tar.gz
mv *.so /usr/lib/firefox/plugins/libflashplayer.so
rm install_flash_player_10_linux.tar.gz

```

So the issue is from adobe then, typical huh?
Frackin adobe

---

### Post by The Eight-Bit Link on 2009-11-29
It came up with another error...
(Sorry!)
 This is it:
 mv *.so /usr/lib/firefox/plugins/libflashplayer.so
mv: cannot move `libflashplayer.so' to `/usr/lib/firefox/plugins/libflashplayer.so': No such file or directory
Could it possibly be in firefox -3.5.3 or firefox-plugins (both are directories)

---

### Post by pissedoffdude on 2009-11-29
> **The Eight-Bit Link said:**
> It came up with another error...
(Sorry!)
 This is it:
 mv *.so /usr/lib/firefox/plugins/libflashplayer.so
mv: cannot move `libflashplayer.so' to `/usr/lib/firefox/plugins/libflashplayer.so': No such file or directory

Add "sudo" (no quotes) in front of that command and it should work.

---

### Post by sandyd on 2009-11-29
> **The Eight-Bit Link said:**
> It came up with another error...
(Sorry!)
 This is it:
 mv *.so /usr/lib/firefox/plugins/libflashplayer.so
mv: cannot move `libflashplayer.so' to `/usr/lib/firefox/plugins/libflashplayer.so': No such file or directory
Could it possibly be in firefox -3.5.3 or firefox-plugins (both are directories)
fixed origional post. there was a typo. (accidentally treated mv as cp.....)

---

