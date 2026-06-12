---
title: "Music player issues"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Epeeman on 2009-01-12
Hey all, great place. I just installed Ubuntu (the newest stable one) and before I made the switch I copied all of my music onto a DVD. When I pulled the files from the dvd into the playlist on the default music player they copied in, but when i played them there was no sound. Master volume = 100% and speakers were on and plugged in

---

### Post by zvacet on 2009-01-12
type in terminal

```
sudo apt-get install ubuntu-restricted-extras
```

and add [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repo to your source list.After that go to the synaptic and in search box type **w32 codec** and install it.When you are finish with that you should be able to play music.

---

