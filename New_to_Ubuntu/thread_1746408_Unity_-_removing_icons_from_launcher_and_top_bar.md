---
title: "Unity - removing icons from launcher and top bar"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by Fraoch on 2011-05-01
There are several items I never use:

- workplace switcher (in the launcher)

- in the top bar: wireless indicator, volume indicator, mail indicator, IM indicator

I've googled and googled - the closest I could find was this:

[http://askubuntu.com/questions/10739/will-it-be-possible-to-remove-add-indicator-applets-from-panel-without-using-sy](http://askubuntu.com/questions/10739/will-it-be-possible-to-remove-add-indicator-applets-from-panel-without-using-sy)

but right-clicking does nothing for me (I tried that first).

I've also taken a look at this:

[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)

nothing there either.

:confused:

---

### Post by LuisGMarine on 2011-05-01
Hello did you try this?  Seem like this might be a winner!  Try it out and let me know!

[http://ubuntuforums.org/showthread.php?t=1734534]("http://ubuntuforums.org/showthread.php?t=1734534")

---

### Post by johnnyredshirt on 2011-05-02
Yes please! I want to remove the IM and email indicators plus the workplace switcher as well . Don't need 'em, don't use 'em, for me a waste of space.

---

### Post by Fraoch on 2011-05-02
> **LuisGMarine said:**
> Hello did you try this?  Seem like this might be a winner!  Try it out and let me know!

[http://ubuntuforums.org/showthread.php?t=1734534]("http://ubuntuforums.org/showthread.php?t=1734534")

Thanks but there doesn't seem to be an option in here to remove the workspace switcher from the launcher or many of the items in the top bar.

---

### Post by Version Dependency on 2011-05-02
I have found a way to get the Workspace Switcher icon to no longer appear in the Unity launcher.  

First, open up a terminal and open gnome-panel by typing:
```
gnome-panel
```
This launches the old gnome panel.  Your gnome  panel should have a Workspace Switcher on it, probably in a 2 X 2 grid  pattern.  (If you don't have a Workspace Switcher on the gnome-panel,  right-click on the panel and add it.)  Now right-click on the Workspace  Switcher on the gnome-panel and select Preferences.  Change the columns  to 1 and the rows to 4.  Now log out of Unity...then log back in.  The  switcher on the launcher will be gone. 

Now your desktop wall will be in a 1 X 4 grid, up to down...rather than  side to side.  But this all I've found to work.  Changing to a 4 X 1  grid side to side will not remove the launcher switcher.  

NOTE: To get the Unity launcher switcher back, simply open the  gnome-panel in terminal again, and go back to a 2 X 2 grid.  Logout and  log back in.

---

### Post by 3177 on 2011-05-02
If your talking about the unity panel (the top bar is called the dock), right click on the icon you don't want, then click remove from panel.

---

### Post by Fraoch on 2011-05-02
> **Version Dependency said:**
> I have found a way to get the Workspace Switcher icon to no longer appear in the Unity launcher.  

First, open up a terminal and open gnome-panel by typing:
```
gnome-panel
```
This launches the old gnome panel.  Your gnome  panel should have a Workspace Switcher on it, probably in a 2 X 2 grid  pattern.  (If you don't have a Workspace Switcher on the gnome-panel,  right-click on the panel and add it.)  Now right-click on the Workspace  Switcher on the gnome-panel and select Preferences.  Change the columns  to 1 and the rows to 4.  Now log out of Unity...then log back in.  The  switcher on the launcher will be gone. 

Now your desktop wall will be in a 1 X 4 grid, up to down...rather than  side to side.  But this all I've found to work.  Changing to a 4 X 1  grid side to side will not remove the launcher switcher.  

NOTE: To get the Unity launcher switcher back, simply open the  gnome-panel in terminal again, and go back to a 2 X 2 grid.  Logout and  log back in.

Great trick!  That worked perfectly, thanks!:D

---

### Post by Version Dependency on 2011-05-02
> **Fraoch said:**
> Great trick!  That worked perfectly, thanks!:D

Glad to be of help.

---

### Post by Fraoch on 2011-05-02
> **3177 said:**
> If your talking about the unity panel (the top bar is called the dock), right click on the icon you don't want, then click remove from panel.

I'm still unfamiliar with the terminology - I had read something on the Internet that I can't find now which described it as the "top bar".  But anyway...

I was referring to the indicators (another web page calls them "AppIndicators").  They are on the top right-hand corner of the screen.  Right-clicking them doesn't do anything, it's the same as left-clicking them.  My understanding is that the AppIndicators must be uninstalled - which is tricky because I don't know what the package names are.

---

### Post by Version Dependency on 2011-05-02
Not sure how complete this list of indicators is, but I bookmarked [this]("http://askubuntu.com/questions/30334/list-of-application-indicators") when I came across it yesterday.   Don't know if it's of any use to you or not.

---

### Post by Fraoch on 2011-05-02
> **Version Dependency said:**
> Not sure how complete this list of indicators is, but I bookmarked [this]("http://askubuntu.com/questions/30334/list-of-application-indicators") when I came across it yesterday.   Don't know if it's of any use to you or not.

Those are very cool - in fact there's a couple I'm going to install, but they seem to be additions to what's there by default.

I guess I've never liked notifications, they remind me too much of the Windows system tray which I despised.  Remember some Windows installs you've seen that have dozens and dozens of crazy little icons there?  Bleh, I hate that look and I made sure any computer I ever had used an absolute minimum of tray icons.

Unity is kind of growing on me but I'm still scratching my head why some of those AppIndicators are there.  I don't use wifi - this desktop is wired - yet I have a wireless strength indicator there.:rolleyes:  I don't use IM or even have a client installed and there's an IM status indicator there.

I wouldn't mind so much if these were easy to remove with a right-click but they're not.

---

### Post by johnnyredshirt on 2011-05-03
Vielen Dank, that gnome-panel trick worked for me. I set it to one desktop, logged and it was gone from the launcher.

---

### Post by Fraoch on 2011-05-03
Well, for anyone looking to remove indicators from the top bar/dock/whatever, you have to UNINSTALL the indicator using your method of choice - I used Synaptic.

The first few were easy - just search for "indicator".

- to remove the indicator showing your user name and IM status, remove "indicator-me"

- to remove the indicator showing the "envelope" and your mail status, remove either "evolution-indicator" or "indicator-messages".  I can't remember which, but both are gone now and so is my "envelope" icon.

- to remove the indicator that looks like a volume control and shows your media player, remove "indicator-sound"

- this last one was tricky...to remove the indicator showing your wireless strength, remove "network-manager-gnome".  This was hard to find and a little scary because I was worried I'd lose Internet access after I removed it.  No, I still have Internet access.

I left the clock and the logout/restart/shutdown "power button".  I suppose these are controlled by "indicator-datetime" and "indicator-session".

---

### Post by mattstat on 2011-05-07
Fraoch,  

Thanks, it worked perfectly.   Now all we need are indicators that return the dictionary and cpu monitor to the "dock".

---

### Post by motherboyxx on 2011-05-07
good post, I hated the grid set up. Does anyone know how to keyboard shortcut the workspace switcher?  I had it done in gnome 3 shell (on 11.04 beta) but cant figure it out in unity.  I have been looking all over the internet and configuration applications...no luck

---

### Post by motherboyxx on 2011-05-07
well crap, now my switcher does not work at all and windows are popping up with no header bars. I have to close windows from Docky or unity dock. I was messing with compiz manager and dont know what i did...any help?

---

### Post by Fraoch on 2011-05-07
> **mattstat said:**
> Fraoch,  

Thanks, it worked perfectly.   Now all we need are indicators that return the dictionary and cpu monitor to the "dock".

No problem.

Don't know about the dictionary as I never used it, but the CPU/memory monitor can be installed by searching for (and installing) "system monitor indicator".  Unfortunately it's not graphical, but that's all there is at this point.

---

### Post by Fraoch on 2011-05-07
> **motherboyxx said:**
> well crap, now my switcher does not work at all and windows are popping up with no header bars. I have to close windows from Docky or unity dock. I was messing with compiz manager and dont know what i did...any help?

I find that Unity can get confused - I have to reboot to fix it sometimes.

---

### Post by mtalexan on 2011-05-14
> **Version Dependency said:**
> I have found a way to get the Workspace Switcher icon to no longer appear in the Unity launcher.  

First, open up a terminal and open gnome-panel by typing:
```
gnome-panel
```
This launches the old gnome panel.  Your gnome  panel should have a Workspace Switcher on it, probably in a 2 X 2 grid  pattern.  (If you don't have a Workspace Switcher on the gnome-panel,  right-click on the panel and add it.)  Now right-click on the Workspace  Switcher on the gnome-panel and select Preferences.  Change the columns  to 1 and the rows to 4.  Now log out of Unity...then log back in.  The  switcher on the launcher will be gone. 

Now your desktop wall will be in a 1 X 4 grid, up to down...rather than  side to side.  But this all I've found to work.  Changing to a 4 X 1  grid side to side will not remove the launcher switcher.  

NOTE: To get the Unity launcher switcher back, simply open the  gnome-panel in terminal again, and go back to a 2 X 2 grid.  Logout and  log back in.

Sounds like it's a dynamically populated icon based on the number of workspaces wide you have setup.  An easier way to get rid of it is to use CompizConfig Settings Manager and go to General Options -> Desktop Size and set the Horizontal Virtual Size to 1.

---

### Post by wildmanne39 on 2011-05-16
> **motherboyxx said:**
> well crap, now my switcher does not work at all and windows are popping up with no header bars. I have to close windows from Docky or unity dock. I was messing with compiz manager and dont know what i did...any help?

Hi, just open a terminal by hitting alt+f2 or ctrl +alt+t and type unity --reset  and let it run for about three minutes, do not worry about the errors it will list, then hit ctrl+alt+del to restart the computer and everything should be fine.:D

---

### Post by wildmanne39 on 2011-05-17
> **motherboyxx said:**
> well crap, now my switcher does not work at all and windows are popping up with no header bars. I have to close windows from Docky or unity dock. I was messing with compiz manager and dont know what i did...any help?

Hi, if your problem or question is resolved, would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.:)

---

### Post by steveparbkk on 2011-05-28
> **Version Dependency said:**
> I have found a way to get the Workspace Switcher icon to no longer appear in the Unity launcher.  

First, open up a terminal and open gnome-panel by typing:
```
gnome-panel
```
This launches the old gnome panel.  Your gnome  panel should have a Workspace Switcher on it, probably in a 2 X 2 grid  pattern.  (If you don't have a Workspace Switcher on the gnome-panel,  right-click on the panel and add it.)  Now right-click on the Workspace  Switcher on the gnome-panel and select Preferences.  Change the columns  to 1 and the rows to 4.  Now log out of Unity...then log back in.  The  switcher on the launcher will be gone. 

Now your desktop wall will be in a 1 X 4 grid, up to down...rather than  side to side.  But this all I've found to work.  Changing to a 4 X 1  grid side to side will not remove the launcher switcher.  

NOTE: To get the Unity launcher switcher back, simply open the  gnome-panel in terminal again, and go back to a 2 X 2 grid.  Logout and  log back in.


Worked for me too!

Thanks

---

### Post by RedLeg217 on 2011-05-29
This really is the bummer with Unity (lack of customization)  I just hope that changes in the future.  As you progress with Unity and become efficient with it, the three apps at the bottom (Workspace Switcher, Applications, Files and Folders) really become pointless and only take up space.

---

### Post by wildmanne39 on 2011-05-29
> **RedLeg217 said:**
> This really is the bummer with Unity (lack of customization)  I just hope that changes in the future.  As you progress with Unity and become efficient with it, the three apps at the bottom (Workspace Switcher, Applications, Files and Folders) really become pointless and only take up space.Hi,you can change those, I will give you link to some guides so you can set it up more to your liking.
[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)
[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)
[http://www.webupd8.org/2011/03/disable-appmenu-global-menu-in-u](http://www.webupd8.org/2011/03/disable-appmenu-global-menu-in-u)

---

