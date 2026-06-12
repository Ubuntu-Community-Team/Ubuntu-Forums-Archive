---
title: "Panel permanently non responding"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by spacebar22 on 2010-01-07
Hi I posted below to Desktop forum but no answer. Any one ANY idea just how I can do anything / find some program to kill the panel and restore a panel from which I can lauch apps?  I can only close session by reset button - this panel is permanently empty and non-responding. And the 9.10 ISO just hangs despite passing test,. How can I even format the disk? 
      

>>> 

I have the same problem on 9.10 with Gnome. I autohid two "taskbars" that were one above the other. On reboot I have a fixed single empty "taskbar", dragging or right-clicking which has no effect. I can open Nautilus by right-clicking a file but can't launch a program (I need Terminal I guess) even with Create Launcher because it wants a command without telling you what the launch command is. The Help button doesn't help indeed suggests you don't need a command whereas there is an error if you don't give one. 

So it seems there is no way out except reinstall? Please give step by step how I might be able to get back the menus that used to be on the taskbar - thanks

---

### Post by Anuovis on 2010-01-07
I do not really know what you did to your existing panels. If they are not locked, you should be able to add almost anything you want. Just right click and select *Add to Panel...* The menus are also there.

If you need to launch anything, you can also press alt+F2 and look for the application from there.

Your panels might just be locked. Press alt+F2 and run the command *gconfig* . You should be presented with *Configuration Editor*.
Go to *Apps>Panel>Global* and see if *locked_down* option is checked. Make sure it is not and try the panels again.

---

### Post by melrokz on 2010-01-07
Do:
```
sudo pkill gnome-panel

```
in a terminal. Good luck. Your panels will restart.

---

### Post by spacebar22 on 2010-01-07
I just autohid the panels on the right click menu which was fine until I rebooted .    
There is only one empty non responding panel. ALT + F2 does nothing.  I cannot access terminal as I said unless someone can tell me the name of the app and the command. I don't know if the help doesn't tell you.  Can some one tell me where in the file system system monitor is, then maybe I can get there and launch it using Nautilus and kill this panel. 

BTW I installed Ubuntu 9.04 in a partition alongside 9.10 using a CD I know works. I did sudo apt-get install cvs and it returns "cant find CVS". So this means that side by side installs are broken too? Windows looks warm and inviting right now... hope I'm wrong. I mean is there no system restore, no way to default the installation....??


Thanks!

---

### Post by Anuovis on 2010-01-07
> **spacebar22 said:**
> ALT + F2 does nothing

You mean, nothing happens when you press this combination? Nothing at all?

If you need the terminal right away, you can also right click on the desktop, choose *Create Launcher* and type in _*gnome-**terminal*_ in the *Command* line. You should get a shortcut to open it.

---

### Post by spacebar22 on 2010-01-07
> **Anuovis said:**
> You mean, nothing happens when you press this combination? Nothing at all?

If you need the terminal right away, you can also right click on the desktop, choose *Create Launcher* and type in _*gnome-**terminal*_ in the *Command* line. You should get a shortcut to open it.

Nope, ALT + F2 has no effect. But it can take several minutes to launch a program with the state it's in now. I got into the terminal using the above. Thanks for that. I did sudo pkill gnome-panel and the panel at the bottom now has the Trash can and help logo flickering but it has no right-click menu and the computer is still too slow to do much. 

gconfig does not seem to be a valid command in the Terminal. Anything else I can try in the terminal?

---

### Post by Anuovis on 2010-01-07
Something is really wrong with your system. It is not the panels.

---

### Post by spacebar22 on 2010-01-07
> **Anuovis said:**
> Something is really wrong with your system. It is not the panels.

All I did was autohide and reboot. 1.3.10 won't install from the ISO. Is there a command just to kill the panel and not start it? And how do you then add a panel from there? 

And system restore? Windows has it, and Mac has Time Machine, so what does Ubuntu have?    

And why can't I apt-get install on a clean install of 9.4?

Looks like I have to format the disk, install 9.4 on its own then use the internal update to get 9.10 which is how I updated from 9.4 initially. 

Any other ideas welcome.

---

### Post by Anuovis on 2010-01-08
I have heard that sometimes upgrades mess up the system. If you did upgrade from 9.04 to 9.10 then the clean install of Karmic would have been better. Is that what you did?

It is not only the panels, you have some weird blinking icons, alt+F2 does not work. Weird.

---

### Post by spacebar22 on 2010-01-08
> **Anuovis said:**
> I have heard that sometimes upgrades mess up the system. If you did upgrade from 9.04 to 9.10 then the clean install of Karmic would have been better. Is that what you did?

It is not only the panels, you have some weird blinking icons, alt+F2 does not work. Weird.

Yes I upgraded 9.04 > 9.10 via internal update. But I see other reports of this problem and I don't suppose they are all upgrades. If there is no system restore then I think there ought to be. This would defeat a complete novice.

---

### Post by Anuovis on 2010-01-09
> **spacebar22 said:**
> Yes I upgraded 9.04 > 9.10 via internal update. But I see other reports of this problem and I don't suppose they are all upgrades. If there is no system restore then I think there ought to be. This would defeat a complete novice.

I have not heard of such thing as system restore. Maybe it is possible to do something like that.

Anyway, a fresh install would only take you 20-30 minutes. And it does not require your presence once you pick the initial settings. I think it would be a good thing to give it a try. 9.04 might be more stable than 9.10. The latter still has bugs and things like that. You can wait till 10.04 and skip Karmic altogether. 

If you want to solve your problems one by one without reinstalling, you could do so. But there are quite a few posts about things going wrong when upgrading, so it is difficult to say which way is easier. You could at least expect to solve some of them by just a simple clean install.

Good luck.

---

### Post by gir9999 on 2010-01-12
you should try what i did in my thread here:
[http://ubuntuforums.org/showthread.php?t=1379354](http://ubuntuforums.org/showthread.php?t=1379354)

i had the same exact problem as you, with all of the same symptoms.

i think it has to do with autohide messing up.

let me know if it works!

---

### Post by doru001 on 2010-01-16
panel autohide makes panels not visible after reboot, and the system slower. I did not upgrade, the install took hours (third try was lucky, first two had I/O failures) on a system where I never had any problems with the CD or HDD, and I checked them completely under Windows. 

You can try: 

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
``` or: 

```
gconftool-2 --shutdown && rm -rf ~/.gconf/apps/panel && pkill gnome-panel
```which i found in other threads. 

Good luck, and hope that in the future we will be able to use autohide.

Bug is filed here: 
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/481643](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/481643)

---

### Post by spacebar22 on 2010-01-21
> **gir9999 said:**
> you should try what i did in my thread here:
[http://ubuntuforums.org/showthread.php?t=1379354](http://ubuntuforums.org/showthread.php?t=1379354)

i had the same exact problem as you, with all of the same symptoms.

i think it has to do with autohide messing up.

let me know if it works!

It works, thanks for your answers.

---

