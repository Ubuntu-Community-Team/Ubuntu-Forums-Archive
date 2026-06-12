---
title: "Cd-rom"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by l.t.elite on 2009-08-24
hi i got ubuntu a little while ago, and i have a question about how i can get cd-roms to run on ubuntu, i read a magazine called total guitar with which comes a free cd/cd-rom it can be used as a cd in a stereo or cd player but on a computer it should automatically open a menu which lets u select video lessons and suchlike, but on ubuntu it wont open the menu and just opens up my media player and shows me the cd content, are there any programs or anything i should try to let me access the video files.
thanks.

---

### Post by verbal.kint on 2009-08-24
There is probably an autostart on the CD that is setup to launch some kind of windows application.

What you could do is install WINE, you can get this if you go to add/remove in the applications menu or if you want to use the terminal type:

```
sudo apt-get install wine
```

Once this is installed if you open the cd there should be a file called autorun or startup or something along those lines, double click on that and if you are really lucky you might be able to see the content

---

### Post by MelDJ on 2009-08-24
I take it that the cd comes with a windows installer or.exe file. .exe files cant be opened in linux unless you have an emulator like Wine.

---

### Post by l.t.elite on 2009-08-25
thanks loads ill give that a try, wish me luck!

---

### Post by MelDJ on 2009-08-25
do reply whether you have suceeded or not;)

---

### Post by tarps87 on 2009-08-25
It is highly likely that the videos are stored on the cd a video file along side any apps.
Could you post the output of
```
ls -R /media/cdrom0
```

---

### Post by sandyd on 2009-08-25
> **MelDJ said:**
> I take it that the cd comes with a windows installer or.exe file. .exe files cant be opened in linux unless you have an emulator like Wine.
**W**ine **i**s **n**ot an **e**mulator

---

