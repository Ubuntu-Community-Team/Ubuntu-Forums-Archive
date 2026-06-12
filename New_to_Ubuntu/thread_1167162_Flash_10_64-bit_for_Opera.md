---
title: "Flash 10 64-bit for Opera"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by rlj399 on 2009-05-22
i finally got flash 10 to work in firefox, but now that i have opera it says i need to download the latest flash player, so i was wondering how to enable it for opera?

---

### Post by benerivo on 2009-05-22
Download the 64-bit flash package from adobe...
[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)
and extract the libflashplayer.so file from it. Then make a folder called /home/YOU/.opera/plugins and place the file in there. In opera, check the plugins section of the preferences, to make sure that the folder location is one of the places that opera checks for plugins.

---

### Post by gandaran on 2009-05-22
if you install the plugin (libflashplayer.so file) in /usr/lib/mozilla/plugins then both firefox and opera can use it, if you want only opera to use it then install in /usr/lib/opera/plugins.

---

### Post by rlj399 on 2009-05-22
how do i check where it is? because it DOES work for firefox, just not opera.
Bythe way, i can't make the file called /home/YOU/.opera/plugins  i get an error saying i can't have slashes in the name

---

### Post by benerivo on 2009-05-22
The flashplugin you have installed now should be in a sub-folder, somewhere inside /usr/lib. An example would be /usr/lib/mozilla/plugins. When you find it, you can just make opera point to that folder in the plugin settings. 

The file name i mentioned is meant to be a folder name. My home folder is located at /home/ben. And my flashplugin (downloaded from adobe labs) is at /home/ben/.mozilla/plugins/libflashplayer.so

So go in to the .mozilla folder and make a new folder called plugins. Then copy the libflashplayer.so file in to it.

---

### Post by rlj399 on 2009-05-22
kk worked thanks!

---

