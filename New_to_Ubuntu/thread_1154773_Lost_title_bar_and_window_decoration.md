---
title: "Lost title bar and window decoration"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by V-600 on 2009-05-10
I have an aspire one running the netbook remix 9.04. When my computer boots up it doesn't have a panel at the top of the screen and any windows I open don't have any window decoration (title bar, buttons etc).

If I change window mode to the standard gnome and then back, it usually gets things working but when the netbook interface starts, it shows the following error


EDIT: I just tried to change back to the netbook remix mode and still have no panel. Not quite sure why.

> Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Could not send message to gconf daemon: Message did not receive a reply (timeout by message bus))

This started happening (as best I can remember) after I tried the suspend feature, or before I first tried the "change desktop mode" feature. These were both around the same time and I can't remember if one specifically affected it.

Many thanks if anybody has any ideas about what to do next.

---

### Post by supermooshman on 2009-05-10
sounds like you got the following problem: [https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519](https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519) 

hope this helps

---

### Post by V-600 on 2009-05-10
Thanks. I had a look round the forum to see if anyone else had had similar probs but didn't think to check if a bug report had been filed. I'll keep an eye on it and see if I can figure out what to do.

---

### Post by pauna on 2009-05-10
> **V-600 said:**
> Thanks. I had a look round the forum to see if anyone else had had similar probs but didn't think to check if a bug report had been filed. I'll keep an eye on it and see if I can figure out what to do.

This should give you detailed instructions: [https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519/comments/85](https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519/comments/85)

---

### Post by digiapb on 2009-06-03
FYI, I was able to recover my title bar by removing (rm -r)the following folders':

.gconfd
.gconf
.gnome2
.gnome2_private
.config

this was also being discussed here:
[http://ubuntuforums.org/showthread.php?t=1138978](http://ubuntuforums.org/showthread.php?t=1138978)

thanks

---

### Post by lka on 2009-06-12
Hello,
I had the same problem.
Testing the netbook remix, go back to ubuntu desktop and the titlebar was gone.

I have solved the problem with deinstalation of Maximus Window Manager.

---

### Post by craig139 on 2009-08-07
I am currently running UNR on an OCZ Neutrino, and ran into the same problem.  It seems to be tied to shutting down the system while in conventional Gnome Interface mode rather than Clutter Interface mode.

> **lka said:**
> Hello,
I had the same problem.
Testing the netbook remix, go back to ubuntu desktop and the titlebar was gone.

I have solved the problem with deinstalation of Maximus Window Manager.

---

