---
title: "Ctrl+Alt+Del replacement in Ubuntu"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by chirag64 on 2010-11-08
OK, so I was playing this game and I changed some of the game's display settings and the screen went white. It stayed white for a couple of minutes but the mouse was responsive.

I tried pressing many keys but that didn't help. I tried doing Alt+Tab and Ctrl+Alt+Del as I would do in Windows, but that doesn't seem to work in full-screen apps in Ubuntu. I even tried Win+D and Alt+F2, thinking this would work, but even they didn't :(

Is there any keyboard shortcut that would supercede the applications so that I can return to my desktop and close them from there, incase they don't respond correctly?!?

---

### Post by mick222 on 2010-11-08
Ctrl +alt +syskey (print screen) +K
press and hold each one in turn will reset your screen and take you to the login prompt. Someone will explain this better.

---

### Post by tea for one on 2010-11-08
Good evening

There is a useful panel application called "Force Quit"

Right click top panel
Select "Add to Panel"
Scroll down to "Force Quit"
Click "Add"
Exit

I hope this helps

Kind regards

---

### Post by Nickjpost on 2010-11-08
Alt+F4 always works for me.

---

### Post by uRock on 2010-11-08
Alt F4 doesn't always work with a locked up program.

---

### Post by sikander3786 on 2010-11-08
> **tea for one said:**
> Good evening

There is a useful panel application called "Force Quit"

Right click top panel
Select "Add to Panel"
Scroll down to "Force Quit"
Click "Add"
Exit

I hope this helps

Kind regards
In addition to this, you can bring up the application launcher by pressing Alt + F2 and type xkill and then just click any unresponsive windows.

You can enable the Ctrl + Alt + Backspace combination to kill X but it would kill all the active applications and bring you to the login screen. So it is of no use here I think.

---

### Post by mick222 on 2010-11-08
You could alao set a keyboard shortcut to xkill (force quit) which will kill the currently running program when you click on it. See here [http://www.youtube.com/watch?v=3X9vvxm5qxQ](http://www.youtube.com/watch?v=3X9vvxm5qxQ)

---

### Post by chirag64 on 2010-11-08
Yeah, **Alt+F4** didn't work...

Force Quit seems nice, but it wouldn't help me in a situation if I'm stuck with a fullscreen program...

**Ctrl +alt +syskey (print screen) +K** seems to do the trick, but I believe the correct key combination is **Alt+Syskey+K,** which I found by a little googling...

Also, **Ctrl+Alt+F2** brings up a fullscreen terminal which can help me kill the app instead of killing the whole X server with the **Alt+Syskey+K **combination, and then return back to the desktop with **Ctrl+Alt+F8**

---

### Post by chirag64 on 2010-11-08
sikander3786: As I mentioned earlier, **Alt+F2** doesn't work if you have a fullscreen program running.

And the **Ctrl + Alt + Backspace** combination does not work in the new versions of Ubuntu. Its replaced by **Alt+PrintScreen+K**

---

### Post by sikander3786 on 2010-11-08
> **chirag64 said:**
> sikander3786: As I mentioned earlier, **Alt+F2** doesn't work if you have a fullscreen program running.

And the **Ctrl + Alt + Backspace** combination does not work in the new versions of Ubuntu. Its replaced by **Alt+PrintScreen+K**
You can always switch to a tty say tty2 by pressing Alt + Ctrl + F2 and type killall followed by your application name (if you know that). e.g,

```
killall wine
```

Edit: You'll need to press Ctrl + Alt + F7 to return to the desktop.

---

### Post by toekneewood on 2010-11-08
You should be able to do **Ctrl+Alt+F1 to Ctrl+Alt+F6**.  These are all different run levels.  Then **Ctrl+Alt+F7** will give you the GUI run level[B].
[/B]
If you go to system, Preferences you will file "keyboard shortcuts".  From there you can change lots.  Be careful not to choose one that might clash.

---

### Post by chirag64 on 2010-11-08
> **sikander3786 said:**
> You can always switch to a tty say tty2 by pressing Alt + Ctrl + F2 and type killall followed by your application name (if you know that). e.g,

```
killall wine
```

Yeah...that works quite well :mrgreen:

---

### Post by chirag64 on 2010-11-08
> **toekneewood said:**
> You should be able to do **Ctrl+Alt+F1 to Ctrl+Alt+F6**.  These are all different run levels.  Then **Ctrl+Alt+F7** will give you the GUI run level[B].
[/B]
If you go to system, Preferences you will file "keyboard shortcuts".  From there you can change lots.  Be careful not to choose one that might clash.

Actually thats the first place I went before posting this question....

But I still don't see the keyboard shortcuts **Ctrl+Alt+F1** to **Ctrl+Alt+F7**?!?

---

### Post by mcduck on 2010-11-08
They are not defined by Gnome's keyboard shortcuts, as they work on much lower level than Gnome does.

And toekneewood, they are not different runlevels. The system only runs at one runlevel at a time. :) These are just virtual terminals, by default you have getty running on first six virtual terminals, providing a text UI, and then X running on seventh virtual terminal for the GUI.

By the way, if many users are logged in at the same time, each user gets their own virtual terminal. So the second logged in user's desktop can be accessed with ctrl-alt-f8, the third GUI would run at ctrl-alt-f9 and so on.

---

### Post by dojida on 2010-12-08
Hi chirag64, I just noticed your post and it solved a problem I was having with foobilliard which also opened up to a blank screen. I posted a query in the "Gaming & Leisure" section but got no replies. I posted a link to your thread and marked mine as solved.

[COLOR="Red"][QUOTE=dojida;10216072]I was looking through the forums and found that chirag64 had a similar problem a few weeks ago in this thread [http://ubuntuforums.org/showthread.php?t=1616628&highlight=keyboard+shortcuts](http://ubuntuforums.org/showthread.php?t=1616628&highlight=keyboard+shortcuts). I tried various options such as ctrl+alt+F2 and typed killall foobilliard (which didn't work), but then I tried ctrl+alt+F7 from the terminal screen and foobilliard came back working correctly. I don't know what happened but I've tried the game again a couple of times with no problems. Anyway, thanks to chirag64 and the guys who responded to his thread. Hope this helps anyone with similar problems. [/COLOR]

---

### Post by chirag64 on 2010-12-09
I'm glad my question helped u, Dojida :)
Even my problem here is solved, so I guess we can mark this thread as solved too :)

---

### Post by Gingalone on 2010-12-14
I got a blank screen and system hanging with Ctrl+Alt+F9...

---

### Post by mcduck on 2010-12-14
> **Gingalone said:**
> I got a blank screen and system hanging with Ctrl+Alt+F9...

Well, it's just a blank screen unless you are actually running that many virtual terminals at the moment. (you need to have at least three users logged in at the same time before the 9th VT is used for anything)

Are you sure the system froze? Did you try pressing Ctrl-Alt-F7 to return to your desktop?

---

