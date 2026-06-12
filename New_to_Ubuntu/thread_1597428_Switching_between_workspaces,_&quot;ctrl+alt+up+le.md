---
title: "Switching between workspaces, &quot;ctrl+alt+up+left&quot; doesn't work"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by NinjaWizard on 2010-10-15
Hi.

In ubuntu I use 2x4 workspaces because I'm so awesome, and I love it (both the workspace setting and being awesome).

I mainly use the keyboard to navigate between the workspaces: the shortcut
ctrl + alt + arrowkeys.

They all work fine, and if I e.g press up + right, ubuntu jumps up diagonally to the workspace that is "north east" from where I started. However, it won't jump "north west", when I use
ctrl + alt + up + left.

I tried searching the forums and google, but any potential solutions out there gets drowned in all the pages containing the relevant words.

Hope someone can give me some pointers on how to fix this.
Thanks!

---

### Post by eriktheblu on 2010-10-15
Are you using Compiz-fusion?

---

### Post by NinjaWizard on 2010-10-15
Possibly, if it's the standard on ubuntu 10.04 Lucid Lynx?
I have a process in top called 'compiz' at least.

If this doesn't answer your question, how do I check?

---

### Post by Ballzac on 2010-10-15
I'm having a similar issue, although I can't use up and down at all, only left and right. I would actually like to set "move up" and "move down" to button4 and button5 respectively so that I can just scroll between viewports vertically or drag horizontally, but I go to the "Desktop-based Viewport Switching" tab of the "Viewport Switcher" menu, and when I set a button to "move up" or "move down", it doesn't do anything.

Alternatively, if there is a command that 'gets' the current viewport location, and another that 'sets' the current viewport location, it would be trivial to set up a command line with a keymap to do it, but I can't find any info on what commands are available other than 'wmctrl', which has capability of changing desktop number and moving windows, but doesn't appear (I tried wmctrl --help) to have anything involving viewport location (actually it does, but I think it means something a bit different to what I want). Still, if it's not working with the installed plugins, I don't see why a command should be able to do it. However, the Expo plugin gets me to any viewport I wish, so the viewports are obviously working.

I'm using compiz-fusion on Maverick meerkat, and currently have 6 horizontal and three vertical viewports.

---

### Post by Ballzac on 2010-10-15
Actually, now that I think about it, I'm a little confused as to where these key bindings are in the ccsm. I can set a key binding or button binding to move left or right via the "Desktop-based Viewport Switching" tab, but even when these are set to "disable", the Ctrl-Alt-Left/Right shortcuts still work.

---

### Post by Ballzac on 2010-10-15
.

---

### Post by SamikMTBSI on 2011-05-20
This bug is not exclusive to switching desktops.

I had noticed for a long time that the "CTRL+ALT+UP+LEFT" shortcut doesn't work as the others.  I found a bug on launchpad for it at one point, but it was dismissed as trivial (I can't find it now...).

However, the bug seems to be more generally related to three-plus key combinations including up+left.

I was playing an old 2d space shooter the other day, and found that, while holding down the spacebar to shoot, I could thurst forward (up arrow) and rotate right (right arrow) at the same time, but could not thrust forward and turn left at the same time.  I could do one, or the other, but as soon as the total number of keys being pressed at the same time reached 3, the UP+LEFT combo stopped working.


I will continuing playing with it a little bit, but it seems clear to me that this has nothing to do with the workspace switcher itself.

---

