---
title: "Exaile abruptly quitting"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by Shmook on 2011-01-04
Any ideas why exaile would crash/close itself when I drag an album from the library to the playlist? This is the only Linux music player I really like and would hate to have to switch. :confused:

---

### Post by kaldor on 2011-01-04
Run it from the terminal and check for errors. 

When you run an application via command line, it shows all the output including errors. Very good way to diagnose issues. Pop up a terminal (Applications > Accessories > Terminal) and run *exaile* and paste the output of the command here.

---

### Post by Shmook on 2011-01-04
Okay perfect, here's what it spat out```
INFO    : Loading Exaile 0.3.2.0...
INFO    : Loading settings...
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
INFO    : Loading plugins...
INFO    : Loading collection...
INFO    : Loading devices...
INFO    : Loading interface...
INFO    : Loading main window...
INFO    : Connecting main window events...
INFO    : Loading panels...
INFO    : Connecting panel events...
INFO    : Done loading main window...
INFO    : Playing file:///media/0DC534677A5F5815/mp%23/La%20Plan%C3%A8te%20Sauvage%20(1973)/06%20-%20Maquillage%20de%20Tiwa.mp3
**
Gtk:ERROR:/build/buildd/gtk+2.0-2.22.0/gtk/gtktreestore.c:1117:IA__gtk_tree_store_remove: assertion failed: (parent != NULL)
Aborted

```
and this happened like I said, when I dragged an album over from "Collection" into the playlist window

---

### Post by Shmook on 2011-01-04
and here's another one! This one happened while a song was playing, doing no other operations...perhaps this one is related to the file? I'm not sure, but it "aborted" again...
```
emw@goobox:~$ exaile
INFO    : Loading Exaile 0.3.2.0...
INFO    : Loading settings...
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
INFO    : Loading plugins...
INFO    : Loading collection...
INFO    : Loading devices...
INFO    : Loading interface...
INFO    : Loading main window...
INFO    : Connecting main window events...
INFO    : Loading panels...
INFO    : Connecting panel events...
INFO    : Done loading main window...
INFO    : Playing file:///media/0DC534677A5F5815/mp%23/The%20Flaming%20Lips%20-%20Clouds%20Taste%20Metallic/Placebo%20Headwound.mp3
python: ../../src/xcb_io.c:249: process_responses: Assertion `(((long) (dpy->last_request_read) - (long) (dpy->request)) <= 0)' failed.
Aborted

```
^^okay not file-related, plays fine in Banshee

---

### Post by kaldor on 2011-01-04
Found this: [https://bugs.launchpad.net/ubuntu/+source/exaile/+bug/440648](https://bugs.launchpad.net/ubuntu/+source/exaile/+bug/440648)

Seems to be a common issue with Exaile on Ubuntu. Not sure what to do, I'll dig around a bit more.

---

### Post by wmeler on 2011-04-10
The bug linked to seems very related to what I posted here.  See the bottom where I have put links to a number of (seemingly) related bugs:

[http://www.linuxquestions.org/questions/linux-software-2/exaile-suddenly-not-working-873425/](http://www.linuxquestions.org/questions/linux-software-2/exaile-suddenly-not-working-873425/)

Hope that helps someone out there.  (As for the covers you lose...there is a Cover Manager that if you Start it, downloads away.  So no real issue there.)

---

### Post by rburkartjo on 2011-04-10
i am using exaile in 11.04b1 and can drag any album and have it play fine with no crashes. do you have the lastest version of exaile? i too also like this player the best

---

### Post by skralljt on 2011-05-17
You are probably asking exaile to do more than it is able.  I know that exaile crashes if I drag more than 500 songs into it, this on a 1.8ghz machine with 2 gigs of ram.  I suspect that you are having the same problem.  I received a similar error which led me here: 
Gtk:ERROR:/build/buildd/gtk+2.0-2.22.0/gtk/gtktreestore.c:1117:IA__gtk_tree_store_remove: assertion failed: (parent != NULL)
If you want to listen to a large collection of music, try amarok with a mysql database, foobar2000 under wine, audacious2, or mpd/ncmpc/sonata.  They all do a better job of dealing with large music collections.  That being said, exaile is still my favorite every day music program because of low resource usage compared to amarok but still very usable with lots of features.  Just noticed the exaile devs got podcasts from feedburner working, can finally listen to podcasts again!

---

### Post by AmadeusHermes on 2011-09-04
Hello you all.

I have used linex for nearly 8 years now and use it 98% of the time. I  am only at user level though even if I have masterd many issues  throughout all this time, but now I have a problem that I can not figure  out.

I decided to use Exaile as my music player (I use VLC for video) and  everything was OK. Somehow one day it happened to crash when I double  cllicked on an mp3 on Nautilus.

Since then I have been watching closely and have realized that Exaile  crashes always with the same mp3s. They are many but they are always the  same ones. These mp3s work perfectly well with any other player, but,  with Exaile, they make the program to open and in a fraction of a second  it closes again. If Exaile happens to be open when I click on these mp3s  it will shut down inmediately.

I have tried to open Exaile through console, if I do this it works perfectly well as it did in the begining when I installed it for the first time.

I have uninstalled and reinstalled but nothing has changed.

¿Can you give me any advice or a place where I might look?

Thank you very much for your work and spirit, you are great!

---

