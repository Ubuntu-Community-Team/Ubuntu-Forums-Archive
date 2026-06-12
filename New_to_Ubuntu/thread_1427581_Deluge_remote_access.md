---
title: "Deluge remote access"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by gottijr on 2010-03-11
-linux newbie-

  I'm using transmission right now. I have remote access with it through web. Considering is what i need it worked good until now

  I've seen very good reviews for deluge

  Question:

  can i remote access deluge from windows laptop? also like web access? or something?

  thanks ... pls advice

---

### Post by Shii on 2010-03-11
I have used Deluge for over a year now, it works great. There are plugins you can use for remote access. For example, here's a Web UI:

[http://forum.deluge-torrent.org/viewtopic.php?f=9&t=425](http://forum.deluge-torrent.org/viewtopic.php?f=9&t=425)

edit: I'm wrong, read below!

---

### Post by Dayofswords on 2010-03-11
deluge rocks

yes you can, you have two choices

[http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient](http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient)
**webui:**
you can connect to deluge through any web browser, see link for setup
(i think you need to turn on the webui plugin)

**Thinclient:**
by default deluge is set to classic mode, which is a few less features. Go to "Preferences -> Interface" and untick "Enable" under "Classic Mode". 

in normal mode you can connect to deluge daemons running and do stuff as if you were using the client there
again see link for setup

the webui and thin client **does not** care what os you are runing to use webui or thin client (eg, thinclient on windows with deluge daemon on linux)

most of the steps on the link you can do in the gui, at school on windows right now so i cant say much more than that
(personally, the thinclient rocks)

---

### Post by Cas07 on 2010-03-12
yep that is the same setup i run and it is awesome :p

Download the latest 1.2.1 version from PPA

The user guides and [support forum]("http://forum.deluge-torrent.org/index.php") have a lot info to get you up and running.

---

### Post by gottijr on 2010-03-17
> **Caos said:**
> yep that is the same setup i run and it is awesome :p

Download the latest 1.2.1 version from PPA

The user guides and [support forum]("http://forum.deluge-torrent.org/index.php") have a lot info to get you up and running.

  thank caos

  it looks like you're already running the deluge 1.2.1 and it looks like a very powerful torrent

  did you installed that using: [http://havetheknowhow.com/Install-the-software/Install-Deluge-Headless-RC.html]("http://havetheknowhow.com/Install-the-software/Install-Deluge-Headless-RC.html") ?

  i fallowed that one but how can i use the scheduler now? What else i have to install?

---

### Post by aeiah on 2010-03-17
> **gottijr said:**
> thank caos

  it looks like you're already running the deluge 1.2.1 and it looks like a very powerful torrent

  did you installed that using: [http://havetheknowhow.com/Install-the-software/Install-Deluge-Headless-RC.html]("http://havetheknowhow.com/Install-the-software/Install-Deluge-Headless-RC.html") ?

  i fallowed that one but how can i use the scheduler now? What else i have to install?

the scheduler is a rather recent addition so you might not find much documentation about it, but you shouldnt need to install anything else for scheduling to work. [i use a script for it](http://aeiah.blogspot.com/2010/03/limit-deluge-based-on-time-of-day.html), on an older version of deluge (1.1.6) that you're welcome to try.

according to the deluge support forums it seems the scheduler cant be set through the webui, you'll have to use the thin client or command line to set things :(

---

