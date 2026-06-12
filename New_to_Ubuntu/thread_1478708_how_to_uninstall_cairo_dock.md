---
title: "how to uninstall cairo dock"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by cbbnewbie on 2010-05-10
i tried cairo dock because it looked nice but now i want to remove it i tried the command sudo apt-get remove cairo-dock then it said that cairo dock is removed i tried to log out because from what they say it is loaded in memory. when i logged in i can still see it and worse it now got a black screen around it and i cant even close it. please help urgently thanks

---

### Post by ankspo71 on 2010-05-10
I think the first thing I would try is to kill cairo-dock.
Open a terminal and type:
```
killall cairo-dock
```
let us know how it goes.

I think a reboot will remove it from the memory. If not, disable/uncheck xubuntu's "Save session for future logins" (wording may be different) in session management before logging out. There should be a prompt like that in the logout dialog.
Hope this helps.

---

### Post by cbbnewbie on 2010-05-10
finished removing it i just went to CTRL+ALT+F1 i dont know what its called then typed sudo *apt-get remove cairo-dock cairo-dock-plug-ins* after that there are some files which are associated with it but not removed the terminal instructed me to use sudo *apt-get autoremove*, i think that did it. Thanks to all

---

