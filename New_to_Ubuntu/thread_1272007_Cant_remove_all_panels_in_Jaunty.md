---
title: "Cant remove all panels in Jaunty"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by hnarwan on 2009-09-21
Hi All,

I've installed AWN and wanted to remove all panels. The last one doesnt have the right click remove option so i understand there's another way to do this.

From what i read i have to follow the instructions below:

1. Goto System -> Preferences -> Sessions
2. Click on Current Session tab. Find gnome-panel there and set it's style to
"Trash" and click Apply button. DO NOT close the Sessions Window
3. Now open a terminal and type:
Code:

$killall gnome-panel

4. Now close the terminal window and go back to the sessions window.
5. Click on the Session Options tab and check (tick) the "Automatically remember running applications when logging out" check-box.
6. Click on the "Remember currently running applications" button.
7. Close the sessions window.


The problem with this is i dont have any 'sessions' utility under Preferences - i read on and see it was renamed to Startup Applications in Jaunty but when i open that i dont see 'gnome-panel' there.

Any ideas anyone?

thanks
Hardeep

---

### Post by SuaSwe on 2009-09-21
Try this:

[http://forum.ragezone.com/f116/tutorial-how-to-remove-gnome-panel-via-ubuntu-545075/](http://forum.ragezone.com/f116/tutorial-how-to-remove-gnome-panel-via-ubuntu-545075/)

---

### Post by hnarwan on 2009-09-22
Thanks Sua, 

But in Jaunty i dont see 'gnome' or 'sessions' in my list of apps...any ideas?

---

### Post by zeroseven0183 on 2009-09-22
Hi hnarwan,

From what I believe, you cannot delete a panel during an active session but you can remove it on your next login. Here's how I manage to do it:

1. press Alt + F2
2. type **gconf-editor**
3. click **Run**
4. in the **Configuration Editor** look for **panel** under **desktop **>** gnome **>** session **>** required_components**
5. right-click **panel **and select **Edit Key..**
6. delete [B]gnome-panel
[/B]7. click [B]OK

[/B]and log-off from your current session and login again.

Of course, be sure you have **AWN** included in the **Startup Applications** first before logging off.

---

### Post by hnarwan on 2009-09-22
perfect! That works a treat!

---

### Post by HarrisonNapper on 2009-09-22
Great! If you can edit the first post, click on Advanced and edit the title to start with [SOLVED]. Thanks!

---

### Post by cajunlibra on 2009-10-25
I tried everything mentioned above and nothing is working.

If I go into the gconf-editor and remove gnome-panel, AWN won't start but the panel still comes up.  Then if I try to "kill-all gnome-panel" the process just starts right back up.

I'm running Jaunty.


Thanks

---

### Post by ripzippysf on 2009-11-03
How can I remove all the panels in Karmic?  I've removed all but the last remaining one and it has nothing on it.  I'm using a dock so it's pointless to have this one panel of wasted space.

---

### Post by WaveMyBlackFlag on 2010-01-12
> **zeroseven0183 said:**
> Hi hnarwan,

From what I believe, you cannot delete a panel during an active session but you can remove it on your next login. Here's how I manage to do it:

1. press Alt + F2
2. type **gconf-editor**
3. click **Run**
4. in the **Configuration Editor** look for **panel** under **desktop **>** gnome **>** session **>** required_components**
5. right-click **panel **and select **Edit Key..**
6. delete [B]gnome-panel
[/B]7. click [B]OK

[/B]and log-off from your current session and login again.

Of course, be sure you have **AWN** included in the **Startup Applications** first before logging off.

out of curiosity... would it be possible to replace the panel value with awn-autostart or avant-window-navigator? i seem to have trouble setting awn to start at login, so is it possible to switch them?

---

### Post by WaveMyBlackFlag on 2010-01-13
nope.

---

