---
title: "Workspace and overlapping windows"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by NinjaWizard on 2010-10-09
Hi.

I would normally google this first, but I don't know what things are called, which makes googling a bit difficult. :)

The problem is when I have a window that is not maximized, and I want to place it at the far right of the work space. I have to do this manually, and it's so easy to get a thin strip on the workspace to the right. This is annoying since even though it's just a thin, thin slice, the panel shows the window etc.

How do I make it harder to get windows overlapping several workspaces?

I hope my explanation was clear enough, and if it isn't I will gladly elaborate. :)

---

### Post by migs73 on 2010-10-09
I think I know what you mean. If you have Compiz installed as your window manager, go to the Compiz config manager, select 'Put' and in that, on the 'Misc options' tab you'll find an 'Avoid off screen' option which I think will sort your problem.

Edit: I just tried it and it does work. Just put your pointer to the edge of you screen and then press Super and 'z' (super is the windows key) and the window will move to that position. If you are slightly over the edge of the screen the window will not overlap into the next workspace.

---

### Post by NinjaWizard on 2010-10-09
I installed compiz, I enabled 'Put' and ticked off on 'Avoid offscreen' but I can't see it had any effect. I played around with the 'Snapping Windows' which makes the windows snap to edges, and they snapped ti the panels at the top and the bottom, but it seems it doesn't recognise the sides of the screen as an edge. Not even if I put a panel there.

---

### Post by migs73 on 2010-10-09
Maybe I should be more specific as to what to do when 'Put' and 'Avoid Overlap' are checked in the CCSM. 
Open your window (minimised) put your pointer to the right hand edge of the screen (as far as it will go) then press Super and 'z'. The windows top right hand corner will then jump to the position of the pointer on the edge of the workspace but will not overlap to the next.

---

### Post by NinjaWizard on 2010-10-09
Ah, now I see what you mean. That worked fine, so thanks!

What I really wanted was some sort of barrier that prevents me from dragging the window outside the current workspace, but your solution is still a major improvement.:KS

---

### Post by migs73 on 2010-10-10
No problem, glad to help. If you are happy with the solution, could you mark the thread a solved please. (Top of the page under Thread Tools).

---

### Post by NinjaWizard on 2010-10-10
Done! :)

---

### Post by NinjaWizard on 2010-10-14
Another solution that was closer to what I first wanted was to simply hold "alt + shift" while moving the window. The window you are moving will then snap to edges, like other windows, panels or even the edge of the workspace.

---

