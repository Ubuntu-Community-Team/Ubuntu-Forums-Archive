---
title: "BloGTK Help"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by 289531.EXE on 2010-01-29
Can someone help me either connect with my blog page. I tried but I don't seem to get anything, or is there a way to install  BloGTK 2.0?

Any help would be useful so I can connect to my blog or if you guys can offer a different program. At the moment I have Blog Entry Poster, but I don't like the way it comes out. BloGTK looks a little more indepth and specific but I don't know since I haven't had a chance to use it yet. :)

---

### Post by Automat2 on 2010-05-29
I had the same problem but I hadn't installed the necessary libraries.

Once I did, BloGTK is running well.

---

### Post by boblizar on 2011-05-07
yeah i was about to dig up some old threads and shout that BloGTK is broken in synaptic/apt repos on maverick 10.10....  looks like im missing glade, and pygtk....  wonder why this package missed calling for the dependencies????????  bleh, looks like im gonna have to compile this one from source.

:popcorn:

installed those 2 backends, still nothing, executing the bin reports gtkhtml2 is not present, synaptic looks empty on that subject.....  ill further work this one out so i can let the ubuntu people know whats up because idk how to build deb packages yet.

[http://askubuntu.com/questions/36640/where-can-i-get-python-gtkhtml2/37620](http://askubuntu.com/questions/36640/where-can-i-get-python-gtkhtml2/37620)

this thread suggests installing the theme linux repository.  done and done, python-gtkhtml2 installs from this repo, and blogtk runs no errors on my system ;-)

---

