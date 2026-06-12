---
title: "Finding Apps in &quot;Start Menu&quot;"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by fafayacity on 2009-04-22
Hello,

I just downloaded Ubuntu 8.04 and I went to the Synaptic Package Manager to install two applications found under the "Amateur Radio (Universe)" heading: Predict & Predict-gsat. The installation was successful but I cannot find the program under Applications. I will appreciate any help. This is the first time I use Ubuntu.

PS: I read from one of the thread another gentleman having the sane issue with a different Amateur Radio software and it was solved by typing 'qrq' in the command line. That was a terminal application and mine is a terminal application as well (I believe).

Thank you

---

### Post by Kobalt on 2009-04-22
In general command line softwares don't have a menu entry. You can customize your menus and add entries using Alacarte. To launch it press Alt+F2 and enter > alacarte

---

### Post by fafayacity on 2009-04-22
Great tip...Now I know how to do that and thank you ...

The problem thouh is I cannot find the installed program at all. I installed it through the synaptic package manager and I cannot find it to run it at all. I was wondering where it was...

Thank you

---

### Post by aeiah on 2009-04-22
if they're command line then open a terminal and type the name in. you can type part of the name and hit tab for auto-complete

terminal is located in accessories i do believe. it may seem daunting, and most software is gui, but i havent used any radio software myself. perhaps you can find a gui alternative if you're lucky.

---

### Post by Kobalt on 2009-04-22
Your predict-gsat application seems to be a graphical application, you should find it in Alacarte. Otherwise, try to launch it with Alt+F2 then predict-gsat

---

### Post by michy99 on 2009-04-22
They are probably in usr/bin/ but it is in your PATH, so all you need is the name.

---

### Post by fafayacity on 2009-04-22
It worked....this is great. I just type the name of the app on the command line of Terminal and it popped up.
Thank you for the help

---

### Post by steve101101 on 2009-04-22
if it actually is a gui you can always make a shortcut icon in the top tool bar if you want to make launching it easier. just right click the panel > add to panel ... > custom application launcher > type in some name, the command you used to run it in the terminal and grab some icon if you want. 

:)

---

