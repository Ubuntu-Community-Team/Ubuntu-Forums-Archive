---
title: "(Symlink?) How to move libflashplayer.so to /usr/lib/mozilla/plugins"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by SpyderX on 2009-01-11
Hi, I currently dont have flash 10 in my comp and want to move the flash 10 beta for ubuntu 8.10 64 bit. This plugin thing (libflashplayer.so) in my desktop. How do I move it to mozilla's plugins folder, because it says accesss is denied when i try to move. I found out that i got to do a symlink to do that, but i dont know how (confusing insturctions for a newbie). Can someone please tell me in detail how I can do this, or what exactly i got to put into the terminal thanks.

---

### Post by igknighted on 2009-01-11
cd Desktop
sudo mv libflashplayer.so /usr/lib64/mozilla/plugins

---

### Post by metallicamike on 2009-01-11
or you can use nautilus, that eliminates the use of the confusing terminal commands...almost.

---

