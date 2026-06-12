---
title: "vlc media player skins"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by ryan andrews on 2011-02-15
well guys 


i downloaded vlc skins and i wanted to copy them into /usr/share/vlc/skins2

but i cant it says error while moving permission denied


and i cannot edit permissions it says you are not owner 

so i want solve this 

please suggest me something 

thanks

Ryan Andrews.:D

---

### Post by jhulf on 2011-02-15
Hi,
to change something in '/usr/share/.. , you need to gain root.

I believe, you can do that with the Terminal through:

```
gksudo nautilus
```
then navigate to the needed folder and put the skin at its place.

This will enable the skins for every user on your pc.
Sometimes there are hidden folders in your homefolder, they can be edited without root. If VLC has a folder there, most likely you can put the skin inside there. This would enable the skin just for yourself.

have fun

---

