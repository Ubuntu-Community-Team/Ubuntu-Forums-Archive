---
title: "Task Bar Stuck To The Right"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by mohab on 2009-02-08
Hi,

When I turned on my computer this morning the task bar(?), or applications menu (Applications, PLaces, System, etc), was stuck vertically to the right of the screen with the red icon at the bottom of the screen and the orange and red Ubuntu icon at the top. 

I have tried dragging the bar to the top, but that doesn't work. I tried shutting down my computer and starting it again, but the bar remains to the right. I have searched these forums and on the net, but did not find a solution. How can I fix this? I'm using Handy Heron, if that makes any difference for finding a solution.

---

### Post by PurposeOfReason on 2009-02-08
Have you tried right clicking an open space and changing the orientation there?

---

### Post by tehforum on 2009-02-08
Right click on the "task bar" > Properties > General> Orientation > Top.

Should work.

---

### Post by mohab on 2009-02-08
> **PurposeOfReason said:**
> Have you tried right clicking an open space and changing the orientation there?

Yes, but see no way to move task bar in the pop up menu options:

*Create Folder, Create Launcher, Create Document, Clean Up By Name, Keep Aligned (Tried that but did nothing), Change Desktop Background (Opened that but saw no way to restore bar to top).

---

### Post by mohab on 2009-02-08
> **tehforum said:**
> Right click on the "task bar" > Properties > General> Orientation > Top.

Should work.

Tried this but can't seem to get enough of a bite on the bar to see the options you listed. I just get pop ups for changing the icons or the Help, Edit Menu, Remove From Panel, etc.

---

### Post by RomeReactor on 2009-02-08
Hi. When you right-click the panel, do you see an option called "Allow Panel to be Moved"? If so, the panel is locked to that position and you must select that option before moving it.

---

### Post by mohab on 2009-02-08
> **RomeReactor said:**
> Hi. When you right-click the panel, do you see an option called "Allow Panel to be Moved"? If so, the panel is locked to that position and you must select that option before moving it.

No, I just get this:

Help
Edit Menus
Remove From Panel
Lock To Panel 

Or

Launch
Properties
Remove From Panel
Lock To Panel

---

### Post by RomeReactor on 2009-02-08
Those options are showing up because you're clicking on an applet. Make sure you right-click in an empty space in the panel.

---

### Post by mohab on 2009-02-08
> **RomeReactor said:**
> Those options are showing up because you're clicking on an applet. Make sure you right-click in an empty space in the panel.

Ufortunately, no matter where I click I get those options and no other choices. I have clicked on empty spaces all over the panel but just get the options I listed.

---

### Post by houstonbofh on 2009-02-08
You need to click on an empty space.  You are getting properties for the icon, not the panel.  Could also be why it won't move with dragging.  Do you have no empty space on that panel?  If so, you can remove a few icons, and add them back later.

---

### Post by RomeReactor on 2009-02-08
Try this: Open a terminal, and run the following:
```
gconftool-2 --shutdown
```
Then:
```
rm -rf ~/.gconf/apps/panel
```
And lastly:
```
pkill gnome-panel
```
That should reset your panels to their default configuration.

---

### Post by mohab on 2009-02-08
> **houstonbofh said:**
> You need to click on an empty space.  You are getting properties for the icon, not the panel.  Could also be why it won't move with dragging.  Do you have no empty space on that panel?  If so, you can remove a few icons, and add them back later.

Ah, I will try this.

---

### Post by mohab on 2009-02-08
Worked! Thanks! And thanks to everyone who helped. 

I Removed the icons and dragged the panel back up to the top.

---

### Post by ajgreeny on 2009-02-08
Glad you got it back, but I am fascinated as to why there was no empty space on your panel, no matter where you right clicked.  Do you have so many taskbar icons and applets that there really is no empty areas, or was there some other strange thing happening?

---

### Post by mohab on 2009-02-08
> **ajgreeny said:**
> Glad you got it back, but I am fascinated as to why there was no empty space on your panel, no matter where you right clicked.  Do you have so many taskbar icons and applets that there really is no empty areas, or was there some other strange thing happening?

I had 4 icons, but seemed not enough space to create the move perhaps because the sides of the screen are shorter than the top and bottom.

---

### Post by dokudoug on 2009-03-30
I had this problem. I'm using a laptop in sultry conditions and I mis-dragged the sucker with a slightly sweaty finger.

No right-click was available because the bar was overloaded with customisations. Very nasty, and quite a trick to escape from.

In the end the command line sequence suggested worked the trick, but at the expense of zapping all my customisations, which I will have to redo.

It was a pain in the a** and disrupted my flow. Talk about the man from Porlock. Free software UIs seem ever to be a bit jerky in comparison to the Mac, and full of forseeable snags.

But we trust the distro ripens as we point them out.

---

### Post by ste_mcleod on 2009-05-22
I just hit the same problem, while trying to rearrange Ubuntu NBR on my EeePC.

To move the panel back to the top, run

gedit ~/.gconf/apps/panel/toplevels/top_panel_screen0/%gconf.xml

(if it's a different panel that has been misplaced, then change "top_panel_screen0" appropriately).

and change the value of the "orientation" "<stringvalue>" property (eg) from "right" to "bottom".

Hope that helps - I've no idea if there's a GUI way to do this.

---

