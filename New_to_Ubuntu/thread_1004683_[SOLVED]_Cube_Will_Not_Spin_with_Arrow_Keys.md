---
title: "[SOLVED] Cube Will Not Spin with Arrow Keys"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by jamiehendrich on 2008-12-07
I'm on Feisty Feist with Compiz Fission.

This morning my cube ceased spinning with my arrow keys.  Also, I don't even have the little four brown boxes to go from desktop to desktop.


I have pushed ALT whilst pressing F2 and typed in "compiz --replace" and then clicked on "Run."  I still cannot use my arrow keys to spin the cube.  It does not go from workspace to workspace.

Anyone have any ideas?  I will tell you that when it quit, I went to "system" and then "desktop effects."  Right now "workspaces on a cube" is checked, but every time I go back into that area, I have to recheck it.  So.....

Jamie

PS  Thank you very much.

---

### Post by residualbit on 2008-12-07
This only thing I can think of, if you said that the four boxes aren't on the panel anymore, would be to right click the pannel, and add the workspace switcher again.

---

### Post by jamiehendrich on 2008-12-07
Okay.  I have done that and added the workspace switcher and have the brown squares.  

  However, my arrow keys will not control that.  I have to utilize my mouse to maneuver from square to square.  Why aren't my arrow keys working?  Any ideas?

Thank you.

---

### Post by T2manner on 2008-12-07
i believe you have to do ctrl alt arrow

---

### Post by jamiehendrich on 2008-12-07
Thank you for the repsonse.  Yes.  I am doing CTRL-ALT plus right or left arrow and no response, zero.    Those keys are not functioning at all.  Any ideas what I have done...........or what my computer did on its own for absolutely no reason.:)

---

### Post by jpoRS on 2008-12-07
Maybe Compiz quit out for some reason, putting you back in Metacity?

Try this-

0. If you haven't already, install the Compiz-Fusion Icon
```
sudo apt-get install fusion-icon
```
1. Run the program.  I believe it is under Applications>System Tools, but I may be wrong.
2. Right click the new icon in your notification area (it should be a little blue box).  Select Window Manager and then select Compiz.
3. Right click the box again and click "Reload Window Manager"

That could fix it.

Good Luck!
jim

---

### Post by jamiehendrich on 2008-12-07
Jim, the compiz program is there.  I typed in ALT F2 at my desktop and typed in compiz --replace and clicked on "run" and the screen blinks.  

I have gone under system, compizconfig manager and enabled the cube effects.  

It's just that the CTRL-ALT-arrow keys are not functioning as they were this morning.  I could use those and flip from cube face to cube face.  All that happened was my computer froze and when I turned it on, that was the result.  

I did a test and right-clicked on the panel, clicked on add to panel and then added the workspace switcher with four workspaces to see if I could just utilize the CTRL-ALT-right/left arrows with the four little brown squares and it does not function.  I can move from workspace to workspace only with my mouse.  

Any ideas?

---

### Post by jamiehendrich on 2008-12-07
PS  Normally when I reboot my computer the words "compiz-fusion (or whatever the title is) comes up in red on my computer.  I am not getting that when I reboot my computer if that is any kind of indicator.

Thank you.

---

### Post by jamiehendrich on 2008-12-07
Really strange but it is working now.  I went several times into "system" then "compizconfig settings manager" and checked "desktop cube and "rotate cube" and then would try it and nothing.  The CTRL-ALT-arrow keys would not function.   Then I would go back in and those same two would need to be checked again.  It was not saving the changes.

Anyway, I have tried it again.  It saved the changes and my cube is spinning properly now.  

Thank you to everyone for your suggestions.  

Jamie

---

