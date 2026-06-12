---
title: "How do I use Conky?"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by thejakeman on 2010-05-02
Hello all, I'm trying to get Conky to work, but I don't know how to start it. I have a file called "conky.conkyrc" in my home folder with the configuration text inside, but that's all that I've done with the program. I found the configuration text stuff on another thread here. So here's all I've done:

Installed Conky
Looked for it in the menus
Didn't find it
Read that I needed a conky.conkyrc file in the Home directory
So I opened gedit, pasted something from [here]("http://ubuntuforums.org/showthread.php?t=281865") and tried to start Conky by going Alt+F2 and typing "Conky" but nothing happened.

What do I do? Thanks in advance!

---

### Post by Girya on 2010-05-02
did you try typing conky with a small c ie conky as opposed to Conky ?

---

### Post by thejakeman on 2010-05-02
Yes I did but instead of giving me the error of not finding it, the run prompt just closed. My desktop remains un-conkified.

---

### Post by Sealbhach on 2010-05-02
The file needs to be called .conkyrc

Here are some simple conky.rc examples:

[http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)

Here's a setup guide for a popular Conky format:

[http://ubuntuforums.org/showthread.php?p=6365702](http://ubuntuforums.org/showthread.php?p=6365702)


.

---

### Post by The Titan on 2010-05-02
You can also use the -c /path/to/config to sully an alternate configuration file.

Here is a link that talks about using conky with fluxbox.  If you scroll down you will see the part about conky and just ignore the stuff about flux.

[http://codedred.com/2010/04/usable-lightweight-interface-using-conky-and-fluxbox/](http://codedred.com/2010/04/usable-lightweight-interface-using-conky-and-fluxbox/)

---

