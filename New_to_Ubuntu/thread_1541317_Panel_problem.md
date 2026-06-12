---
title: "Panel problem"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by rvgsd on 2010-07-29
Hi, 
I recently installed Xubuntu 10.04 (32 Bit) on my Dell Studio 15.
It was working absolutely awesome, until I thought of using just one(at the bottom) panels instead of two. I removed the bottom
panel and customized the top one to appear at the bottom, and it vanished!
I restarted the system,but it still was not there. If I do 'alt+f2' and then start the xfce4-terminal and then in the terminal I start xfce4-panel, the panel appears again, until I close the terminal. 
When I directly start the panel from Run('alt+f2'), it appears for a fraction of second and disappears. 
Help please!

---

### Post by byStanderone on 2010-07-29
...dissappearing panels in xubuntu: [http://anujpathania.blogspot.com/2008/06/xubuntu-panels-disappear.html](http://anujpathania.blogspot.com/2008/06/xubuntu-panels-disappear.html)

---

### Post by rvgsd on 2010-07-29
Hi, thanks for the reply, but this does not work. (Maybe it did with the previous XFCE versions.)
It still disappears. 
I also tried adding the xfce4-panel to the auto start, it still opens with a terminal, closing which makes the panel disappear.
Also the panel started using the terminal shows only on 1 of my 2 virtual desktop.
I don't want to have to reinstall Xubuntu again just because my Panels disappeared..! 
Any help will be appreciated.
Thanks.

---

### Post by 4Orbs on 2010-07-29
First, remove the new entry you added for the panel in the startup apps settings. Then....

Maybe this will work. Start the panel with the terminal, then reboot while leaving the terminal and panel open on the desktop. When you login again you should be able to then close the terminal, and the panel will remain working.

---

### Post by rvgsd on 2010-07-29
No, still when I restart, and close the terminal, the panel disappears. 
This happens after I install MATLAB and configure everything else. I can't imagine doing everything all over again :( .

---

### Post by 4Orbs on 2010-07-29
Start the panel with the terminal using this command:
```
killall xfce4-panel && xfce4-panel &
```
Then reboot while the terminal and panel are still open.

---

### Post by 4Orbs on 2010-07-29
And don't even think of reinstalling the entire system just for a panel problem.

---

### Post by rvgsd on 2010-07-29
> And don't even think of reinstalling the entire system just for a panel problem.

Thanks for trying to help! 

> start the panel with the terminal using this command:
```
killall xfce4-panel && xfce4-panel &
```

When I did this, it said that this process is not running, so I did only ```
xfce4-panel & 
```, and restarted. The problem still persists.

---

### Post by 4Orbs on 2010-07-29
Did you remove the panel entry in the autostart application settings? That doesn't need to be there.

It would probably be easiest to simply delete the panel completely, then build a fresh one. First, make sure you can right-click on the desktop and get an applications menu to open up.

If you'd rather keep trying to fix the existing panel, that's ok too. My guess is that one or more of the applets is causing the problem. You don't have the panel set to auto-hide, do you? First thing to delete would be the desktop-pager applet since it's only showing one desktop but you actually have two. Delete it (right click on it and select "Remove"). Before you reboot, open the xfce4 settings manager and in the Sessions and Startup section, make sure the option to "Remember Running Apps" is NOT checked.
Also, when you click the reboot button, make sure the little checkbox beneath the buttons "Automatically Save This Session" is NOT checked (NOTE: My wording might not be correct)

---

### Post by rvgsd on 2010-07-29
Yes I removed the entry from the auto-start before I tried you solution.

The panel is not set to auto-hide. I can access the menu on right clicking the desktop.

I will try deleting this panel and adding a new one...

---

### Post by 4Orbs on 2010-07-29
Ok. When you add the new one, at first it will be only a tiny square on the desktop.

---

### Post by rvgsd on 2010-07-29
Tried adding a new panel, it also has the invisibility power..behaves the same exact way..no difference..
You have anymore ideas ??

---

### Post by 4Orbs on 2010-07-29
Were you able to see it for even one second?

---

### Post by 4Orbs on 2010-07-29
Try opening the panel again with the terminal. It should be just the little square new panel now. Don't bother customizing it yet. Leave the terminal and panel open.

Reboot, but first put the check back in the box to remember this session.

When you log back in, look at the terminal and see if it still shows the xfce4-panel command. It should not. It should only have yourname@yourcomputer:~$
If that is the only thing on the terminal, you should be able to close the terminal without closing the panel.

---

### Post by rvgsd on 2010-07-29
Yeah, when I see the new panel as a square. 
When I restart the system, the terminal shows up with:
name@name-laptop:$

so I know no command is running on it. Still, when I close this terminal, the panel disappears.
One thing I noticed is before I close the terminal, If I open something else, like google chrome or Thunar, then the Panel stays open until the last thing (whatever it is : chrome, thunar, etc) stays open. As soon as the last window is closed, the panel disappears.

Now I am clueless..! Help!

---

### Post by 4Orbs on 2010-07-29
I'm at a loss. Maybe customizing the new panel will force it to stay open.

Suggest adding these applets. Notification Area, Task List, Mixer Applet and a Spacer (non expanding). Set the panel to Fixed Position, Full Width, with the alignment to bottom-left. Reboot with the terminal and panel still open. After login try closing the terminal. Hopefully the network manager daemon will force the panel to remain visible.

---

### Post by rvgsd on 2010-07-29
Tried that with no luck.
Appreciate you help though..
Anyways, at this moment I am shifting to M$ doze..dual boot..

---

### Post by 4Orbs on 2010-07-29
There are still some things you can try. At your login screen, after you click on your username but before logging in, you can select a different session at the bottom of the screen. Right now it should say "Xubuntu Session". Try switching to the "Xfce Session" and login. Then logout and try the "Xubuntu Session" again. You can repeat the process with the Gnome, Failsafe and any others you feel brave enough to try.

If none of that works, you might try creating a new user account and login to that account. The default 2 panels should work fine for that user. Then logout and login back into your original account. If that still doesn't fix it then you might just try uninstalling the xfce4-panel through Synaptic Pkg Mgr, reboot and open synaptic again and click on status then remove the old configuration files (obsolete). Reboot again, then use Synaptic to install the xfce4-panel again. When you reboot and login, you should be greeted with both panels.

And if that doesn't work... it would probably be best to wait for someone else to reply to your thread. They'll most likely have a quick and easy solution that I am unaware of.

---

### Post by rvgsd on 2010-07-30
Tried creating a new user, with a new name.. then restarted the system, it didn't go the the login screen but it said something like that ubuntu needs to run in low graphics mode, and offered options to reconfigure graphics or run in console. I chose reconfigure and then nothing happened! Same screen appears when I restart. 

Creating a new user makes perfect sense to me as well, I am not a newbie. I cannot imagine I did something wrong! :) been using Xubuntu for over a year now.  Cannot spend more time on this, have to study for my exams next month! 

Seems like a fresh install is only the option, which maybe I'll go for after a couple of months..

All this just because I changed the Panel position! This seems to be a serious issue to me, which needs to be addressed and rectified (I wish I could..)> This issue would certainly deter new users to switch to this (otherwise) good OS.

---

