---
title: "audio cd playing problem"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by usman idrees on 2008-12-31
hi 
when ever i insert an audio cd and double click on a song, it goes to totem movie player, it streams over there but does not play any song.i donot know what to do. can i use totem player as audio player ?
plz reply.....

---

### Post by charleskw on 2008-12-31
Go to system>administration>hardware drivers... then, see if you have any drivers or restricted drivers to install. If so install them. I don't exactly know what that does, but it worked for me.

---

### Post by zvacet on 2009-01-01
If you didn´t installed it yet do it now

```
sudo apt-get install ubuntu-restricted-extras
```

and add Medibuntu repo to your source list like it is described [here.]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by jocheem67 on 2009-01-01
In "preferences"  ---- "standard applications" or something like that ( I've got a Dutch translation here ) you could also make Rhythmbox the default for multimedia.....When I insert an audio cd a window pops up which asks me with what app. to open the cd btw..

I don't think this is codec-related.

Does the cd give an icon on the desktop, ie is it mounted properly?

---

