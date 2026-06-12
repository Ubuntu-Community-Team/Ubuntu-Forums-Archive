---
title: "Gnome -shell not working"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by vivek40 on 2010-08-27
Hii I am trying to use gnome-shell on my lucid. I had installed it earlier and was using it properly through the ricotz ppa, but then one fine day I went ahead and uninstalled it. Today however i felt like having it again and so installed it again using:-
sudo add-apt-repository ppa:ricotz/testing
sudo add-apt-repository ppa:ricotz/testing
and then when I type gnome-shell --replace , the screen flashes for a minute and i 
get the same desktop back again, not gnome-shell.. I get the following bug in the terminal

mutter:6963): mutter-WARNING **: Could not load library [/usr/lib/mutter/plugins/libgnome-shell.so (libgirepository-1.0.so.0: cannot open shared object file: No such file or directory)]
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

can someone please help!

Regards
Vivek

---

### Post by Peter09 on 2010-08-27
I think there are problems bulding gnome-shell - and there have been for a few weeks. The Ricotz ppa seems to be dead at the moment. All activity I can see is coming from people who are building it themselves. This is a shame as I am using the shell, but really do not have the time to build /rebuild/debug it.

---

### Post by Peter09 on 2010-08-27
Note : - have you tried running the following command in a terminal
 
```
gnome-shell --replace
```
 
EDIT: Sorry - just noticed that you have tried this.

---

### Post by vivek40 on 2010-08-27
Actually I feel that it has something to do with mutter. In fact sometime back I had tried installing unity on my desktop just for having a look after uninstalling gnome-shell, and I believe it installs a different version of mutter, but I had purged unity soon after . Would it be possible that it has something to do with this.

---

### Post by vivek40 on 2010-08-27
Ok so I removed mutter and reinstalled gnome-shell which installed mutter again and now the error that comes on the terminal is different:-
[HTML]
Cannot register the panel shell: there is already one running.
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
[/HTML]

---

### Post by Peter09 on 2010-08-27
Your best bet is to go to this thread and discuss with them.
 
[http://ubuntuforums.org/showthread.php?t=1476241](http://ubuntuforums.org/showthread.php?t=1476241)

---

### Post by vivek40 on 2010-08-27
Thanks peter

---

