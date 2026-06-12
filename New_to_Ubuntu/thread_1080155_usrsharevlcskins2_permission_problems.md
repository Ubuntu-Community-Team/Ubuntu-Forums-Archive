---
title: "usr/share/vlc/skins2 permission problems"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-02-25
i am trying to add some skins for vlc. when i try to add them to usr/share/vlc/skins2 i get the message that i am not the owner and cant add.root is the owner/tks cheesemaker

---

### Post by x33a on 2009-02-25
try it with sudo.

---

### Post by rburkartjo on 2009-02-25
x33, tks but that didnt work i have to chown the directory and dont know how/cheesemaker

---

### Post by x33a on 2009-02-25
post the output of 
```
ls -l usr/share/vlc/skins2
```

---

### Post by rburkartjo on 2009-02-25
x33 as you requested

ray@ray-desktop:~$ ls -l /usr/share/vlc/skins2
total 180
-rw-r--r-- 1 root root 125330 2008-10-16 08:09 default.vlt
drwxr-xr-x 2 root root   4096 2009-02-08 06:21 fonts
-rw-r--r-- 1 root root    167 2008-10-16 08:08 skin.catalog
-rw-r--r-- 1 root root   9465 2008-10-16 08:08 skin.dtd
-rw-r--r-- 1 root root  31843 2008-10-16 08:08 winamp2.xml
ray@ray-desktop:~$ 

tks/cheesemaker

---

### Post by billgoldberg on 2009-02-25
Don't change permissions.

You can add the skins in a folder in /home.

Open up Nautilus (Places -> Home) and press "ctrl +h".

Then look and see if there is a ".vlc" folder (notice the dot before vlc).

In there there should be a skins folder.

--

If there for some reason is not, you can open Nautilus as root and paste the skins in that folder.

```
gksu nautilus
```

Now I do see to remember that you'll need to launch VLC using this command:

```
vlc -I skins2
```

for the skins to work.

You could change the entry in your menu to use that command.

Go to "system -> preferences -> Main Menu".

Find VLC, right click it and choose properties.

Remove the command and enter the one I give here.

---

### Post by rburkartjo on 2009-02-25
bill tks have to go back to work will try what you suggested when done and if it works give you a tks and mark this thread as solved/cheesemaker

---

