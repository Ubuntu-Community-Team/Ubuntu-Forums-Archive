---
title: "Unity Crash"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by BJones007 on 2011-04-17
My Unity desktop just crashed a few mins ago. I enabled the desktop cube in Compiz Desktop Manager and it worked fine, but then I accidentally selected I dunno what and now nothing works. There's no panel or desktop icons, everything's gone. I tried opening the terminal, but alt + f2 doesn't work either. Am I gonna have to do a fresh install or can it be fixed. Please help.

---

### Post by tordeu on 2011-04-17
Unfortunately, I might not be able to really help you, because I don't know which compiz setting might have cause that.

What I can tell you is this:

If Alt+F2 does not work, you should be able to access a terminal with
```
Strg+Alt+F1
```And go back to the graphical interface with
```
Strg+Alt+F7
```This way, you should always be able to reach a terminal to enter stuff.

The compiz settings are in the directory
```
~/.gconf/apps/compiz
```You might not remember the exact option you changed, but do you remember where you changed something before everything broke? What is in the window with the compiz cube?

---

### Post by Blasphemist on 2011-04-17
I did this to myself a few days ago. And this is the third I've seen today on the same thing. I got the following from someone else that had the same issue. 

> Start ccsm and disable unity and wall. ccsm will stay open. now enable cube and rotation, then enable unity, expo and window decoration. You might need to enable more plugins(move window, resize window etc.). You need to have the latest compiz and unity

Before he sent it to me, I logged into classic and basically did these same things in ccsm (CompizConfigSettingsManager). I wasn't smart enough to do it all in just one restart. Basically, I used ccsm in classic to re-enable the unity plugin and related, logged into unity and finished getting anything back to normal, then going back to classic and getting it back to normal, such as de-selecting unity in it. This should work for you.

---

### Post by Blasphemist on 2011-04-17
BTW, as he experienced, when in the middle of this nothing seems to work in unity. No key combinations seemed to do anything, none I knew at least such as those mentioned above.

---

### Post by BJones007 on 2011-04-17
> **tordeu said:**
> Unfortunately, I might not be able to really help you, because I don't know which compiz setting might have cause that.

What I can tell you is this:

If Alt+F2 does not work, you should be able to access a terminal with
```
Strg+Alt+F1
```And go back to the graphical interface with
```
Strg+Alt+F7
```This way, you should always be able to reach a terminal to enter stuff.

The compiz settings are in the directory
```
~/.gconf/apps/compiz
```You might not remember the exact option you changed, but do you remember where you changed something before everything broke? What is in the window with the compiz cube?
Ok thanks. What I wanted to do was try to run Compiz in the terminal and restore the default settings to unity, but when I did it said 
```
 fatal: couldn't open display. 
``` 
What could be the possible cause for this?

---

### Post by tordeu on 2011-04-17
Check out the post by Blasphemist above__[]("http://ubuntuforums.org/member.php?u=1165520"). As he has experienced this problem, the solution he posted might work for you as well.

If everything fails, uninstalling and reinstalling compiz and/or unity might be a solution before trying a complete reinstall. But as Blasphemist says, it seems to be a "common" problem.

---

### Post by BJones007 on 2011-04-17
UPDATE:

I fixed it guys. What I did was ran ccsm in the terminal and switched back over to the display. The apport came up and I selected the option to restart Compiz. Once it came up I just opened the default gedit file and voila everything is back to normal once more. Thanks for the help.

---

### Post by tordeu on 2011-04-17
That was faster than I had hoped :D Glad to see it's working again.

---

### Post by BJones007 on 2011-04-17
Same here. Thanks again. 

FOOTNOTE:
I'm having another prolem though, but I'm gonna post it in a next thread. Hope you can help.

---

### Post by Blasphemist on 2011-04-17
> **BJones007 said:**
> UPDATE:

I fixed it guys. What I did was ran ccsm in the terminal and switched back over to the display. The apport came up and I selected the option to restart Compiz. Once it came up I just opened the default gedit file and voila everything is back to normal once more. Thanks for the help.

In my case, I couldn't get to the terminal. I'd like to know how you did it just in case I screw it up again and so I'll know if I see of someone else that has.

---

### Post by BJones007 on 2011-04-17
Sure. Just press alt+ctrl+f(1-5) and login.

---

### Post by laurion on 2011-05-10
I had the same problem 5 minutes ago, and that's how to fix it:


[LIST]
[*] Press ```
 Ctrl + alt + F1
``` to bring up the terminal, and then login with your password and username.
[/LIST]

[LIST]
[*]Remove everything like compiz, compiz-gnome, compiz-...
[/LIST]
```
sudo apt-get remove compiz
sudo apt-get remove compiz-gnome
...

```
[LIST]
[*]Remove every piece of unity, unity-2d, unity-2d-panel, ......
[/LIST]
```
 sudo apt-get remove unity
sudo apt-get remove unity-2d
sudo apt-get remove unity-2d-panel
.....
```
[LIST]
[*]Reinstall unity: ```
sudo apt-get install unity-2d
``` and unity-2d-default-settings ```
sudo apt-get install unity-2d-default-settings
```
[*]Restart the computer:   sudo reboot
[/LIST]
And that's it!

 [SIZE=1](maybe weren't all these things strictly necessary, but that's what i did and it worked) [/SIZE]

---

