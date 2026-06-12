---
title: "A couple of problems that have started recently"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by hobo89 on 2009-02-23
About a week or so ago Firefox started being very slow and unresponsive. Starting it from the terminal, it gave a message about DCOP something or other (I can't remember exactly, without having to restart the computer) but with some help from google I found a fix, launching dcopserver from the terminal before starting Firefox every time I start the computer up (hence I can't get the exact error message without restarting the computer). Now, I have no idea what this means, all I know is it solves the problem. But having to do it every time I boot the computer is a pain.

Another problem I have discovered over the past couple of days is with Amarok (perhaps would have started at the same time as the Fx problem but I hadn't used Amarok in a while). When I launch Amarok, I get the error message "Cannot talk to klauncher" and I get no icon in the tray for it. I tried launching it through the terminal and this is the output:
> Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?
I'm guessing, since these problems probably started around the same time, that something I did back then has caused this. But I have no idea what it could have been. If anyone has any ideas it would be much appreciated. I'm still fairly new to Linux, but I'm pretty comfortable with with it, provided people tell me exactly what I'm doing, not just give a bunch of instructions with no explanation.
Thanks.


Edit: After searching google for a possible fix to the klauncher error, it appears I have managed to solve both problems. I have no idea what I actually did, but I used these commands in the terminal:
$ dcopserver_shutdown 
$ kdeinit 
It appears to have fixed whatever the dcopserver problem was with Fx too. Guess I'll see how it goes.

---

### Post by hobo89 on 2009-02-24
It seems after booting up the computer this morning, the problems still remain, although I know a little more.
I had to first run dcopserver from the terminal to get Fx working properly. Running this is what then causes the 'cannot talk to klauncher' issue, and so have to run dcopserver_shutdown (Fx continues to work fine after this, confusing, at least to me) and kdeinit. I've not encountered any problems since, but it will be a pain if I have to enter these commands everytime I boot up. Has any one got any ideas for a permanent fix to this? Thanks.

---

### Post by hobo89 on 2009-02-28
I decided to try out KDE, and it at first seemed to fix this issue. However today it has started again (using KDE 4.1 if that makes any difference).
Any one have any ideas yet?

---

