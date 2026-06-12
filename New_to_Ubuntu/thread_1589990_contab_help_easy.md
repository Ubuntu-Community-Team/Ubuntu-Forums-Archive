---
title: "contab help easy"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-10-07
okay trying to learn crontab
when i go to the terminal and enter crontab -e
the crontab  opens

okay how to i use the navigations commands at the bottom (e.g. ^G,^X. etc)

when i enter ^G nothing happens i know i am overlooking something/tks

---

### Post by Hippytaff on 2010-10-07
are you using nano to edit the contrab file?

---

### Post by rburkartjo on 2010-10-07
hip yes

---

### Post by rburkartjo on 2010-10-07
solved by me here is a link to answer my question
[http://mintaka.sdsu.edu/reu/nano.html](http://mintaka.sdsu.edu/reu/nano.html)

---

### Post by CharlesA on 2010-10-07
That ^ is normally the "control" key.

Don't forget to mark it as solved.

---

### Post by Paddy Landau on 2010-10-07
You can get crontab to use your usual GUI editor. In the following examples, I assume that you use gedit.


[LIST]
[*]**One-off:** Use the following command to start the crontab editor.
```
VISUAL='gedit' crontab -e
```
[/LIST]

[LIST]
[*]**Permanent:** Add the following line to your .bashrc file.
```
export VISUAL='gedit'
```Start crontab as usual.
```
crontab -e
```
[/LIST]

---

### Post by rburkartjo on 2010-10-07
tks for the info paddy

---

