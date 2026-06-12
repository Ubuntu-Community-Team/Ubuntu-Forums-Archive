---
title: "Totem UI Rewrite?"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by TuxIsCute on 2011-03-04
Hi guys and girls out there!

Um, I would like to have a minimal user interface in a maximized Totem window (no a fullscreen window but very similar).

Now I know that there isn't a UI theme system in Totem so I was wondering how hard it would be to simply rewrite the UI.

Like I said, the fullscreen UI is about what I'm looking for but in a maximized window.  So I'd like to hide the menubar until ALT or some other button sequence is pressed, and have a single tools bar at the bottom of the screen.

I figure the menubar hiding might already exist in a plugin somewhere (I have yet to look).  But the rewriting of the UI at the bottom is what I'm looking for.  How hard would that be?

---

### Post by doas777 on 2011-03-04
seems like it might be a better bet to write your own ui for a cli based player like mplayer, that way you dont have to analyze the existing totem source before even getting started.

ultimately your question comes down to how deeply the UI is integrated into the applications backend functionality. if it is done correctly, the ui is just a thin wrapper around the functional code, but that may not be the case.

---

