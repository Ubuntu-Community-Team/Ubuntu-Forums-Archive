---
title: "Compiz Fusion Help"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by Drastic2010 on 2010-04-04
So all I want to do is get the Desktop cube to rotate.  I've checked Desktop Cube and Rotate Cube in ccsm, but with no luck.  I have also provided 4 workspaces.  I have used ccsm before with absolute ease, but for some odd reason, I have no clue what is going on...

Best regards, Chase

---

### Post by overdrank on 2010-04-04
Hi and welcome, moved to Absolute Beginner Talk

---

### Post by Hamchan on 2010-04-04
Well, what is it doing when you try to change workspaces? Are you stuck on one workspace or are you able to switch but the workspaces are on a wall rather than a cube?

Remember to make your workspaces a 4x1 rectangle when using the cube.

---

### Post by Drastic2010 on 2010-04-04
Yes, it has the 4 workspaces, but like you said it's stuck on the wall rather than a cube.

---

### Post by Hamchan on 2010-04-04
When I said 4 workspaces, I meant four workspaces in a single line as opposed to the square that is common for desktop walls.

Is Desktop Wall or Desktop Plane enabled?

---

### Post by Drastic2010 on 2010-04-04
No, Desktop Wall or Plane are enabled.  However, I do remember coming across a person having a problem with Viewpoint Switcher being checked, so I unchecked that and still no solution.

---

### Post by louis--taylor on 2010-04-04
install simple-ccsm:
```
sudo apt-get install simple-ccsm
```

run it ```
simple-ccsm
```
(or go to the "system>prefrences>Simple CompizConfig Settings Manager" menu)

Click on the 'Desktop' tab
There should be a drop down menu, and you can choose ether desktop wall or desktop cube.

Hope this helps :)

---

### Post by Drastic2010 on 2010-04-04
Ok so I installed simple ccsm, and once I got to the Desktop tab "Desktop Cube" was already in the drop down menu.  So I suppose that shows I have the current settings already enabled, so could the problem lie within drivers (I don't see why it would if i've done desktop cube before)?

Thanks and sorry for the nubness here :P

---

### Post by admiralspark on 2010-04-04
Heh, I love this question. Press Ctrl + Alt + LeftMouseButton, and while holding them all move the mouse around to rotate the cube. You MUST hold all three keys simultaneously though.

---

### Post by morrcahn on 2010-04-04
You must have already tried this but have you checked what you have your shortcuts set on in ccsm. Make sure you are not activating the "unfold" option instead of the regular cube. When you do unfold it lays it out in a wall format like you were talking about.

---

### Post by Drastic2010 on 2010-04-04
Well under *cssm -> rotate cube -> bindings*, the initiate command is <control><alt>button 1, I also unchecked the unfold layout.  I'm wondering if it is because I installed it from Synaptic instead of terminal because not even wobbly windows is working?

---

### Post by admiralspark on 2010-04-04
> **Drastic2010 said:**
> Well under *cssm -> rotate cube -> bindings*, the initiate command is <control><alt>button 1, I also unchecked the unfold layout.  I'm wondering if it is because I installed it from Synaptic instead of terminal because not even wobbly windows is working?

Sorry if it seems like a noobish-suggestion, but did you move the mouse around while pressing Ctrl + Alt + LMB? Because I've met MANY new-to-Compiz users (including myself) who didn't do that and therefore assumed it didn't work. Until you move the mouse, the desktop will appear the same while holding down the keys. 

If that's not an issue, there are several compiz guides on here that have troubleshooting sections, I suggest you try searching the forums or Google for one?

---

### Post by quadproc on 2010-04-04
> **Drastic2010 said:**
> Well under *cssm -> rotate cube -> bindings*, the initiate command is <control><alt>button 1, I also unchecked the unfold layout.  I'm wondering if it is because I installed it from Synaptic instead of terminal because not even wobbly windows is working?
If wobbly windows is not working, and you have System > Preferences > Appearance > Visual effects set to extra, then you are probably not running a correct driver.  You can check the Driver section in /etc/X11/xorg.conf file to see what it is using.

One other thing needed to make the cube work: your zoom must be set to something different than the default.  To find the zoom go to ccsm, click on rotate cube (the illustration) and look at the bottom of the new window.  Set the zoom value to roughly 0.3.  Also, make sure that the box next to rotate cube is checked.

quadproc

---

