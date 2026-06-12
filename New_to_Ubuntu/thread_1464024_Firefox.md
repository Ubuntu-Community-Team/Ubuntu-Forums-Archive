---
title: "Firefox"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by Raymond Ellerton on 2010-04-27
Hi i am new to ubuntu and Fire fox . Yesrterday i was online and doing all the things i wanted to do but today firefox will not open anything even the ubuntu help pages . what am i doing wrong

---

### Post by nhasian on 2010-04-27
if firefox is not working, how are you posting on the forums here?  :)

If you've somehow borked firefox, you can start from scratch by deleting or moving the ~/.mozilla/firefox folder.  enter this command from a terminal:

```
mv ~/.mozilla/firefox ~/.mozilla/firefox.backup
```

then start up firefox again and you'll be good to go.

---

### Post by lovinglinux on 2010-04-27
See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#General-Troubleshooting-Steps-2) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by kmsalex on 2010-04-27
Also if you have solved your problem with firefox remember to use the forums tools to mark this thread as "SOLVED".

---

### Post by takisan on 2010-04-27
Yes, mark it as solved, and how could you have not used Firefox before.

Be sure to get Flash, Java (although it might be pre-installed,) and a bunch of addons.

---

### Post by kmsalex on 2010-04-27
```
sudo apt-get install ubuntu-restricted-extras

```
copy and past that into the terminal (but i would recommend installing [lovinglinux]("http://ubuntuforums.org/member.php?u=649167")'s firefox add on foxruner [http://lovinglinux.megabyet.net/?page_id=527](http://lovinglinux.megabyet.net/?page_id=527))
when it askes for your password the letters woun't show up its for security reasons just type it and hit enter. that will install flash mp3 playback and a few other goodies.

---

