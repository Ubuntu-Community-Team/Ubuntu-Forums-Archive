---
title: "Songbird"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by nene7 on 2010-02-24
hi to all,
 i am usign songbird and i tried to allow the option of manager files to organize all my music files in the default music folder but for some reason don't let me do.

-----------
 Ubuntu 9.04 "Karmic Koala" in Dell inspiron 6400

---

### Post by bruno9779 on 2010-02-24
It is written there in the purple strip.

You are choosing "import to" and "import from" folders to be inside of each other. This would create a loop, so the error.

Basically "/Songbird_music folder cannot be inside of /music

---

### Post by nene7 on 2010-02-24
The loop is error of the songbird program, so that i have to select other folder to do or you have and idea to eliminate this?

thanks

---

### Post by bruno9779 on 2010-02-24
It is not an programming error. If you import music from a folder to itself you create a loop.

It would be a programming error letting you do what you are trying, because it would duplicate your music till your disk is full.

So, yes, you HAVE to choose different folders

---

### Post by warp99 on 2010-02-24
> **nene7 said:**
> The loop is error of the songbird program, so that i have to select other folder to do or you have and idea to eliminate this?

thanks

The reason is because you have a space between Songbird and Music for your directory. Change the name of the directory to Songbird_Music, then point to that directory and you should be fine.


Edit: You need to also disable watch folders for changes or choose another directory.

---

