---
title: "Undocking app windows from top panel"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by rhageman on 2010-07-05
Hi everyone,

I just did the upgrade to Ubuntu 10.04 and got a surprise.  All my application windows want to dock to the upper left corner of the screen.  They seem to be fastened to the top panel, they can't be moved.

I've been dabbling in 9.04 for sometime and have never seen this.

I've DL'ed the manual and am searching for a clue.

Any help would be appreciated.
Thanks

---

### Post by Leppie on 2010-07-05
i'm not sure what you mean, but the following should set the panel to its defaults:
```
gconftool-2 --recursive-unset /apps/panel | killall gnome-panel

```

---

### Post by rhageman on 2010-07-05
Okay, when launching a new application, its window now always opens in the top left corner of the screen on top of any other window that is already open and on top of that corner of the top panel.

If I have a pidgin window open and I try to open Ubuntu help, the help window opens on top of the pidgin window and neither can be moved on the screen.

---

### Post by Leppie on 2010-07-05
hmm... this issue sounds familiar, i had it once or twice. don't remember how i fixed it this instant...

---

### Post by Crazedpsyc on 2010-07-05
have you tried just right-clicking on the thin line before the window buttons, un-checking Lock To Panel, right-click there again and say move. then move cursor to bottom panel

---

### Post by mikewhatever on 2010-07-05
Looks like the windows picker applet got installed. Have you, by any change 'upgraded' to the netbook edition?

---

### Post by rhageman on 2010-07-05
Thanks for your efforts guys, they are appreciated.

Just did a restart from the Windows side of this and all the sudden the Ubuntu windows were behaving normally.  What changed?  I have no idea.

But things look normal now.

Thanks again.

---

### Post by Leppie on 2010-07-05
haha, the wonders of IT...

---

