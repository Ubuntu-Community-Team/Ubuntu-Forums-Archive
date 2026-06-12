---
title: "getting rid of real player in super ubuntu"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by showman47 on 2009-02-01
I've been trying out the 'super ubuntu' distribution, which I like, but it has real player (which I hate) and want to remove it completely.

Since it wasn't installed using synaptic manager I will have to remove it myself, but I want to make sure it is completely removed. It annoyingly is set as the default video application and I REALly (pardon the pun) want to get rid of it.

I know basic linux command line stuff, but I want to make sure I get rid of it's appearance in the menus (i.e. when you right click and choose 'open with' context menu)

Just need to know where to delete stuff and what files to edit.

Thanks in advance.

---

### Post by sandyd on 2009-02-01
```

https://player.helixcommunity.org/2005/help/playerfaq.html#mozTocId185549

```
scroll down to bottom of page :)

then download the script and run it in terminal.

P.S. your uninstalilng the BIN

---

### Post by showman47 on 2009-02-01
Thanks for that, however there are some problems for me with the uninstall script, and I don't fancy debugging it.

I know what files and directories to remove, but what I would like to know (as a matter of interest as well as I'm learning linux) how to remove the entry for 'RealPlayer 11' from the context menu.

i.e. when right clicking on a video file, remove the entry for RealPlayer 11 and disassociate RealPlayer as an application to play videos. I assume this means editing a config file somewhere. would be greatful if you could point me in the right direction.

thanks

Showman47

addendum: I got the uninstall script to work - but it did not remove 'Open with RealPlayer 11' in the menu.

---

### Post by GMachine_24 on 2009-02-01
I have not used "super ubuntu", but .... did you try the old-fashioned way of getting rid of something that shows up on the "applications" list?

that is....

Right-click on "applications" on the upper icon bar ....and select "edit menus" ... from the left pane on "main menu" select "sound and video" and then remove the checkbox from the right hand "items" menu next to "real player" if it is still there, or better yet, right click on the real player item and select "delete"....

You also might check the /usr/bin folder to see if the "realplay" file is still there . . . and since you have removed the real play software you can remove realplay from /usr/bin without any adverse consequences.

Hope this helps.

---

### Post by showman47 on 2009-02-01
Thanks GMachine_24

Stupid me didn't realise removing an app from the menu also removes it from the context menu - clever ubuntu.

Just for reference if anyone searches and finds this thread, the problem I had with the script was that it expected a 'lib' directory in the realplayer directory, and there wasn't one, so it aborted.

I edited the uninstall script (uninst.sh) and changed line 411 from:

for i in codecs common lib mozilla plugins; do

to:

for i in codecs common mozilla plugins; do

i.e. removed the search and removal of a 'lib' directory

after this change, the script worked and removed RealPlayer.

thanks again for the help

---

### Post by GMachine_24 on 2009-02-01
Would you mind marking your post as "SOLVED" so others can see an answer was found. It's always helpful when searching through community forum posts...

glad I could be of help

--gm

---

