---
title: "Panels"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by daniell59 on 2009-06-26
For some reason much of my panel items have been deleted. Could someone please explain to me how I can get them back. In particular, I want to be able to go from one window to another.

Thanks

PS I am trying to learn, but this is all new to me.

---

### Post by saj0577 on 2009-06-26
> **daniell59 said:**
> For some reason much of my panel items have been deleted. Could someone please explain to me how I can get them back. In particular, I want to be able to go from one window to another.

Thanks

PS I am trying to learn, but this is all new to me.

You can right click on panels and select add to panel.


As for restoring not sure if there is a way I have always in the past re added my apps.

Workspace switcher is the one you want to swap from one desktop to another and window select to select individual programs.

Saj

---

### Post by drs305 on 2009-06-26
> **daniell59 said:**
> For some reason much of my panel items have been deleted. Could someone please explain to me how I can get them back. In particular, I want to be able to go from one window to another.

Thanks

PS I am trying to learn, but this is all new to me.

If your panels are gone or very messed up, you can try this:
```
killall gnome-panel  # Refreshes the panels
```

If you want to add shortcuts to the panel, right click an empty part of the and select the shortcut you want.

To switch between windows, you probably mean "Window List" which puts each open app on the lower panel (right click, add to panel, 'Window List').

If you meant switch between desktops/workspaces, that is 'Workspace Switcher'.

Once you have the panels set the way you want them, you can save them to a file (example: panels on your Desktop):
	To save: 	```
gconftool-2 --dump /apps/panel > **~/Desktop/panels**
```
	To restore: 	```
gconftool-2 --load **~/Desktop/panels** && killall gnome-panel
```

---

### Post by daniell59 on 2009-06-26
In particular, how do I get back the printer icon?

Thanks

---

### Post by drs305 on 2009-06-26
> **daniell59 said:**
> In particular, how do I get back the printer icon?

Thanks

Heh - we didn't cover that one. It should appear in the 'Notification Area' when it's connected. You can also add this one with a right click. It's also where your connected network appears.

---

### Post by daniell59 on 2009-06-26
Since I am confused, I would appreciate if someone could look at my snapshot and get me back on track.

Thanks

---

### Post by daniell59 on 2009-06-26
> **daniell59 said:**
> In particular, how do I get back the printer icon?

Thanks

Also, I can find nothing about adding a printer.

---

### Post by daniell59 on 2009-06-26
> **daniell59 said:**
> Also, I can find nothing about adding a printer.

Just found the printer icon in custom toobar

---

### Post by -kg- on 2009-06-27
Well, your top panel is a bit of a mess, and really the only thing you're missing from the bottom panel is your "Window List" (which shows the running tasks, as it does in Windows) and your "Workspace Switcher," which, if you're only using one desktop, you don't really need anyway.

These can both be installed by right-clicking on the panel and selecting "Add To Panel" from the menu.  This will open a dialog/list from which you can select the above applets and install them to the panel.

First add "Windows List" which will install the W.L. applet and display your open windows, just like Windows does in the taskbar.  Left-click and hold on the vertical dashes to the left of the W.L. and drag it over next to the "Show Desktop" icon (which you already have, all the way to the left), then right-click it and check "Lock To Panel."

If you want it (i.e., if you want to use more than one desktop), then right-click on the panel all the way to the right, near and to the left of the "Trash" icon, and select "Add To Panel."  From the menu select "Workplace Switcher" and add it.

Your top panel has a few problems.  First off, let's deal with your "Printer Icon."  This icon is usually displayed in the "Notification Area," of which you seem to have two.  The Notification Area is normally at the right of the Top Panel and is delimited by a vertical line of of 3 dashes.

I notice you have two sets of these, one in front of the "Main Menu" icon (the one that looks like an Ubuntu symbol with the down arrow to the bottom left...you don't need this, BTW, because it is included in the custom "Menu Bar"..."Applications" is the exact same menu) and includes not only the "Main Menu" applet, but also contains 2 Clock applets (you only really need one), the "Fast User Switch" applet (you do need this one), and your "Volume Applet."

You then have a second set of these dashes, which I believe delineates another "Notification Area" and apparently contains your "Network Manager" icon.  Now you have a super amount of room in your first "Notification Area," so right click the vertical dashes on your second notification area (the one to the extreme right) and make sure the "Lock To Panel" box is unchecked.  Then left click and hold and drag it to the left and see if your Printer notification icon is hiding in it.

You only need one Notification area.  The Printer icon and the Network Manager Icon are similar to Windows task icons to the right of the taskbar.  They are running tasks which are minimized to icons and are set to launch at boot time.  Since you have your N.M. (Network Manager) running in one N.A. (Notification Area) and the other N.A. has nothing in it that is a running process, we're going to delete that instance of N.A. and leave the one with the running application in it, since we don't want to accidentally lose your Internet connection.

I'm going to make this a multiple post, since I don't know what if any limitations on post length this board has.

---

### Post by -kg- on 2009-06-27
[COLOR="Red"]_NOTE:_[/COLOR]  Before performing the below, read over it and right click in the larger notification area and make sure you can find the applets I'm talking about.  I'm using Jaunty and don't know what distro you're using, so the names of the applets *might* be different.  If they are, and you can't absolutely figure out which app you really need to install (especially "User Switcher") then don't do the following and come back here and ask.

Also, I apologize in advance if I sound like I'm talking to a Newbie when you might not be one, but I figure better to be safe than sorry, and if a Newbie has the same problem and happens across this, the extra hand-holding might be appreciated by him/her.

OK, to continue:

I assume you've expanded the right-hand N.A. (the one with N.M. in it) as far as you can to the left.  Take note of any icons that may have been hidden, though I don't expect there to be any more, since I tried to slide mine way to the right, and couldn't hide any icons...it just stopped sliding.

Right click on the vertical dashes to the left.  This is the one in front of your "Main Menu" icon.  Select "Remove From Panel."  Don't worry about the applets listed in it; we're going to recreate them in the remaining N.A. panel to the right.

You will be left with the N.A. to the extreme right.  Left-click and hold on the vertical dashes and place them around a third of the way from the right (you don't really need *near* the space that you had originally) and make sure the N.M. icon is all the way to the left of that space.  If you need to move it, right-click on it and make sure that the "Lock To Panel" check box is unchecked, then left-click and drag it into position.

Right-click on the far right of the N.A., select "Add To Panel," and from the list find and select "User Switcher" (or something similar...I don't know what version of Ubuntu you're using).  That will place the applet in the N.A. that allows you to switch users/shutdown or reboot computer/etc.  Make sure this locates all the way to the right of the panel.  Again, drag it into position if necessary.

Next, right-click just to the left of the User Switcher, select "ATP" (Add To Panel) and from the list select "Clock" from the list.  This will add the clock app which shows time and date (which currently you have two of...just install it once, unless you *really* need two).  Move this to the right, as close as you can to the User Switcher.

Next you want to repeat the above and from the list install "Volume Control."  This will complete the Notification Area installations, and you should have at least the default applets installed there.  Network Manager will show up there, as well as the printer icon, since they are both launched at boot time.  If you think you need more (or less) space in the N.A., then drag the vertical dashes in the appropriate direction.  Once you have everything where you want it, be sure to right-click everything and check "Lock To Panel."

Now, the rest of it is easy:

I notice that you have two Custom Menu bars.  You only need one.  Right-click on the one to the right and select "Remove From Panel."  The one to the extreme left is the one that is normally there by default, and they will both contain the same menu selections.

You also have two Firefox icons.  You only need one of those, as well.  If both of them work the same, I would erase the smaller one and leave the larger (easier to see and click on).  All this should leave you with a default set of icons and applets, plus an icon to easily launch Firefox.  Make sure all these icons and applets and the Notification areas are locked to the Taskbar when you get them in the position you want them.

Now, one more thing:

I assume you've found that clicking the printer icon under the toolbar launched the app and put an icon in the N.A.  If you reboot and find it is no longer there, you will need to click on "System/Preferences/Startup Applications."  I have an HP printer, and in the list I have a selection called, "HP System Tray Service."  If you have a different brand, look for something similar in the list and make sure the box is checked.

I think I've covered it.  Any other questions? Just post!
):P

---

### Post by daniell59 on 2009-06-27
> **-kg- said:**
> [COLOR="Red"]_NOTE:_[/COLOR]  Before performing the below, read over it and right click in the larger notification area and make sure you can find the applets I'm talking about.  I'm using Jaunty and don't know what distro you're using, so the names of the applets *might* be different.  If they are, and you can't absolutely figure out which app you really need to install (especially "User Switcher") then don't do the following and come back here and ask.

Also, I apologize in advance if I sound like I'm talking to a Newbie when you might not be one, but I figure better to be safe than sorry, and if a Newbie has the same problem and happens across this, the extra hand-holding might be appreciated by him/her.

OK, to continue:

I assume you've expanded the right-hand N.A. (the one with N.M. in it) as far as you can to the left.  Take note of any icons that may have been hidden, though I don't expect there to be any more, since I tried to slide mine way to the right, and couldn't hide any icons...it just stopped sliding.

Right click on the vertical dashes to the left.  This is the one in front of your "Main Menu" icon.  Select "Remove From Panel."  Don't worry about the applets listed in it; we're going to recreate them in the remaining N.A. panel to the right.

You will be left with the N.A. to the extreme right.  Left-click and hold on the vertical dashes and place them around a third of the way from the right (you don't really need *near* the space that you had originally) and make sure the N.M. icon is all the way to the left of that space.  If you need to move it, right-click on it and make sure that the "Lock To Panel" check box is unchecked, then left-click and drag it into position.

Right-click on the far right of the N.A., select "Add To Panel," and from the list find and select "User Switcher" (or something similar...I don't know what version of Ubuntu you're using).  That will place the applet in the N.A. that allows you to switch users/shutdown or reboot computer/etc.  Make sure this locates all the way to the right of the panel.  Again, drag it into position if necessary.

Next, right-click just to the left of the User Switcher, select "ATP" (Add To Panel) and from the list select "Clock" from the list.  This will add the clock app which shows time and date (which currently you have two of...just install it once, unless you *really* need two).  Move this to the right, as close as you can to the User Switcher.

Next you want to repeat the above and from the list install "Volume Control."  This will complete the Notification Area installations, and you should have at least the default applets installed there.  Network Manager will show up there, as well as the printer icon, since they are both launched at boot time.  If you think you need more (or less) space in the N.A., then drag the vertical dashes in the appropriate direction.  Once you have everything where you want it, be sure to right-click everything and check "Lock To Panel."

Now, the rest of it is easy:

I notice that you have two Custom Menu bars.  You only need one.  Right-click on the one to the right and select "Remove From Panel."  The one to the extreme left is the one that is normally there by default, and they will both contain the same menu selections.

You also have two Firefox icons.  You only need one of those, as well.  If both of them work the same, I would erase the smaller one and leave the larger (easier to see and click on).  All this should leave you with a default set of icons and applets, plus an icon to easily launch Firefox.  Make sure all these icons and applets and the Notification areas are locked to the Taskbar when you get them in the position you want them.

Now, one more thing:

I assume you've found that clicking the printer icon under the toolbar launched the app and put an icon in the N.A.  If you reboot and find it is no longer there, you will need to click on "System/Preferences/Startup Applications."  I have an HP printer, and in the list I have a selection called, "HP System Tray Service."  If you have a different brand, look for something similar in the list and make sure the box is checked.

I think I've covered it.  Any other questions? Just post!
):P


Sorry that I was not able to read this until now. Thanks for the input that you provided me. I will print it out, thus making it easier for me to follow. I am very new to this, and I am sometimes overwhelmed.

---

### Post by daniell59 on 2009-06-27
> **daniell59 said:**
> Sorry that I was not able to read this until now. Thanks for the input that you provided me. I will print it out, thus making it easier for me to follow. I am very new to this, and I am sometimes overwhelmed.

Forgot to mention, I am using Ubuntu 9.04

---

### Post by -kg- on 2009-06-27
Well, since we're both using the same distro, all the operations and what you're looking for will be identical.  If this helps you, then I'm more than happy to help.

I remember when I was near the beginning...it was confusing for me, too.  I've been into computers since the early '80s (before Windows existed) and primarily used MSDOS and Windows.  It was hard for me to make the transition, but it *does* get easier.

---

