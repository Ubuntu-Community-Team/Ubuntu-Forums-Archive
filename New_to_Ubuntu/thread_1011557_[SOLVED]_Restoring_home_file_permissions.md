---
title: "[SOLVED] Restoring home file permissions"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by chavon20 on 2008-12-14
Hi all, is there a way that I can restore the default file permissions in my home folder?  I did a right click, then permissions in my home folder and changed folder access I believe.  So now when I log in (I can still login ok btw) I get this message:
> 
User's $HOME/.drmc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other users.

Is there a quick way that I can restore it to the way it was, even to the systems file permissions default?  I think this may have affected my firefox because my bookmarks in my bookmark toolbar don't appear and I can't go backwards or forwards.

It was easy enough to change the settings, can I change it back easily enough?  Many thanks!

---

### Post by drs305 on 2008-12-14
Follow the steps in this tutorial. It's pretty simple but there is background information on how it happened and how to fix it:
[Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?t=976610")

Same info in ubuntu wiki format:
[dmrcErrors]("https://help.ubuntu.com/community/dmrcErrors")

---

### Post by chavon20 on 2008-12-14
Thanks!  I think that did the trick!  I didn't get that message when I logged back in.  Now just have to figure out what went wrong with firefox...  Can you help?  The bookmarks aren't appearing in the bookmark toolbar and I can't go backwards or forwards.  Also it doesn't seem to remember the most recent pages that I have visited.  Could the change of permissions affected Firefox' ability to remember what I have visited?

---

### Post by drs305 on 2008-12-14
If you happened to have run firefox as root instead of a regular user it is possible the session was stored in root's config files rather than your own. If you now log in as a regular user things should return to normal although you won't have the history files, etc from the root session. 

It wouldn't fully explain the loss of all bookmarks, although you could do a search for bookmark files on your system to see if they ended up in another profile. My guess is there is another profile somewhere on your system with your stored information but I'm not a firefox expert.

---

