---
title: "vlc opens video in new window"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by babloo75 on 2009-05-21
Whenever I open a new file in vlc media player, it opens in a new window. this has started happening since i upgraded to ubuntu 9.04. till 8.10 it was running fine.
the controls are in different window and at times it becomes very annoying to change the volume. everytime i have to minimize the video window and open the vlc main window to change volume.
please help.
(I have attached a screenshot to show the problem i am facing.)
Please help me to avoid this problem.
Thanks in advance.

---

### Post by tad1073 on 2009-05-21
There is an option in preferences to allow only one instance of vlc

---

### Post by babloo75 on 2009-05-21
it is already ticked. but still plays the video in another window and not the parent window.i have just changed the screenshot. the primary vlc window is at the back and the video window is at the top of it. How can i play the video in the same window.
Thanks.

---

### Post by aos101 on 2009-05-21
This seems to be a known bug:

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/314038](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/314038)

Apparently they deliberately disabled the video integrated into the interface because it was crashing, but it seems they left the option there in the vlc preferences (why leave in an option which you know doesn't work?).  It looks like it is fixed in a newer version of vlc, but will not be fixed in Ubuntu Jaunty.

---

### Post by kpkeerthi on 2009-05-21
You may install it from this [PPA]("https://edge.launchpad.net/~c-korn/+archive/vlc") to fix the issue.

---

### Post by babloo75 on 2009-05-21
Thanks. will have to wait for this bug to be removed. hope they remove it at the earliest. till then will have to use totem player.

---

### Post by andrew.46 on 2009-05-22
Hi babloo75,

> **babloo75 said:**
> Thanks. will have to wait for this bug to be removed. hope they remove it at the earliest. till then will have to use totem player.

I suspect this will not happen in Jaunty, although I will be pleased to be proved wrong :-). Are you not keen to use the suggested PPA? I did not use this one myself but I attach a screenshot of vlc 1.0.0 rc1 in action with a single window to give you some encouragement!

Andrew

---

### Post by binbash on 2009-05-22
[http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html](http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html)

---

### Post by babloo75 on 2009-05-22
> **binbash said:**
> [http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html](http://www.ubuntu-inside.me/2009/04/howto-fix-integrated-video-bug-at-vlc.html)

How to proceed with these instructions.

---

### Post by babloo75 on 2009-05-22
do we have to type them in terminal, or what?

---

### Post by andrew.46 on 2009-05-22
Hi babloo75,

> **babloo75 said:**
> do we have to type them in terminal, or what?

I have not tried or tested the vlc in the medigeek's PPA but if you want to add it to your sources.list perhaps the easiest way is:

System --> Administration --> Software Sources --> Third Party Software

and add the line:

deb [http://ppa.launchpad.net/medigeek/ppa/ubuntu](http://ppa.launchpad.net/medigeek/ppa/ubuntu) jaunty main

in this location and press the button 'Add Source'. I assume that you are running Jaunty? I attach a screenshot to illustrate this. There are several PPAs offering updated vlc at the moment so do a little research on the forums before committing yourself perhaps.

All the best,

Andrew

---

### Post by allspamme on 2009-06-02
Thanks that worked.

---

### Post by babloo75 on 2009-06-03
Thanks a lot. Its working fine now.

---

