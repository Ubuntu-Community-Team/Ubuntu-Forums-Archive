---
title: "Screen, isn't, &quot;composited.&quot;, run, compiz, &quot;(-fusion)&quot;"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by kareem_09 on 2009-09-17
So  I know you're probably sick of this hehe but umm I'd really appreciate your help !
Every time I reboot I get the same error message Screen, isn't, "composited.", run, compiz, "(-fusion)". I looked up older posts and I used the compiz -- replace and it works temporarily, when I reboot.. same problem. Also when I go to the hardware manager it says no proprietary drivers are in use on this system. Thanks in advance :)

---

### Post by RealG187 on 2009-09-17
I think when I shut down I see that message as I am shutting down, but I ignore it as the system shuts down normally and boots up normally the next time I boot.

I see this is your first post, Welcome to the forums...

---

### Post by theozzlives on 2009-09-17
Go to System > Preferences > Startup Applications and put ```
compiz --replace
```in there.

---

### Post by CatKiller on 2009-09-17
Or press **Alt-F2**, run ```
gconf-editor
``` and change the **/desktop/gnome/applications/window_manager/current** and **/desktop/gnome/applications/window_manager/default** keys to **/usr/bin/compiz**, so that you aren't having to start two window managers every time you log in.

---

### Post by kareem_09 on 2009-09-23
Sweet thanks everyone! it works great  :D

---

