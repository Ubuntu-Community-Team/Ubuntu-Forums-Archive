---
title: "Taskbar gone...how do I get it back?"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by sagewells on 2010-10-07
I was once a Windows user, and you could right click on the bottom task-bar and do an autohide feature.  So, I tried it, but I now have Ubuntu....well, I can't get it back!  I only can get online by hitting F1, typing "help" in the search bar and clicking on "get more help online..."

I posted on here a couple of weeks ago, and can't find my old post to see if anyone responded (how do I find that?)  I did see someone elses post that had the same problem.  The solution was to hit Alt + F2 and type "gconf-editor".  Navigate to aps>panel>toplevels>top_panel_screen0  and then uncheck the box next to auto_hide.

Many attempts to do this, but nothing even happens.  I mean, from Alt + F2, nothing!  No panel comes up or anything.

Any help is greatly appreciated,
Thank you.

---

### Post by cgroza on 2010-10-07
To check your thread you can go to Search >> Find all your Threads.

---

### Post by andrewthomas on 2010-10-07
Enter in a terminal (or ALT+F2 check run in terminal and copy and paste)
```
 
rm -r ~/.gconf/apps/panel

```
 
To restore the panel to the defaults.

---

### Post by NightwishFan on 2010-10-07
You may need to also reset the panel. Press alt+f2 and type:
```
killall gnome-panel
```

---

### Post by sagewells on 2010-10-07
> **andrewthomas said:**
> Enter in a terminal (or ALT+F2 check run in terminal and copy and paste)
```
 
rm -r ~/.gconf/apps/panel

```To restore the panel to the defaults.


Wow! You guys respond quick!  I tried what you said, but when I hit Alt + F2 nothing happens at all.  There is no terminal to type anything into.  Any other suggestions?  Thanks.

---

### Post by themusicalduck on 2010-10-07
Which version of Ubuntu are you using?

I looked through gconf editor and found the value in a slightly different place that you mention in your post, but I am using the Maverick beta. I wouldn't think it would be different. Which is the post that you got that info from?


This command sets the auto-hide to off on my system -

```
gconftool --type Boolean --set /apps/panel/toplevels/top_panel_screen0/auto_hide false
```

You need to put that into a terminal, if you can't open a terminal, try pressing ctrl+alt+t and then paste that line into the terminal.

If you can't open a terminal that way, you'll need to press ctrl+alt+f1 and type the code in manually.

If it doesn't work straight away, try typing pkill gnome-panel into the terminal.

edit: I'm assuming with this post you mean you have autohide on the top panel, not the bottom panel, which I assume would need this code instead -

```
gconftool --type Boolean --set /apps/panel/toplevels/bottom_panel_screen0/auto_hide false
```

---

### Post by andrewthomas on 2010-10-07
> **sagewells said:**
> Wow! You guys respond quick! I tried what you said, but when I hit Alt + F2 nothing happens at all. There is no terminal to type anything into. Any other suggestions? Thanks.
 You seem to have a weird problem.  You could press (CTL+ALT+F2) then log into your username then type 
rm -r ~/.gconf/apps/panel
 
then 
 
(CTL+ALT+F7) to get back to gnome-desktop and issue the kill cmd

---

### Post by sagewells on 2010-10-08
> **andrewthomas said:**
> You seem to have a weird problem.  You could press (CTL+ALT+F2) then log into your username then type 
rm -r ~/.gconf/apps/panel
 
then 
 
(CTL+ALT+F7) to get back to gnome-desktop and issue the kill cmd


Thanks, I'll try that....might be a couple of days before I can get back on here, but I'll let you know if it works.

---

