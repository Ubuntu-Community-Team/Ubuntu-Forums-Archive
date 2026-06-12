---
title: "Oops deleted bottom panel"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by fisheater on 2009-11-07
Hi, 

I am sheepish about this one, thanks for helping out.

I have deleted the bottom panel from my desktop (the one that shows what programs are open). I was trying to close some open windows and I deleted it by mistake.

The issue now is I cant get it back, when I minimize an open window it vanishes, and my ALT+TAB can not scroll through the windows that are open!

Thanks for your input!

FE

---

### Post by wojox on 2009-11-07
Need to add to panel Window List.

---

### Post by jmszr on 2009-11-07
fisheater,

Right click on an open space on the top panel, click on New Panel, the new panel should appear to the side, right click on the new panel and click on Properties, under Properties click on Orientation - bottom. Right click on the new bottom panel and then Add to Panel to replace what you had there originally.

---

### Post by blazemore on 2009-11-07
Hit Alt + F2, and type
```
gksu debconf gnome-panel
```

Then log off and on again.

---

### Post by fisheater on 2009-11-07
Thanks for all the input!

blazemore - your solution produced the best result - my panel was restored, the open applications could be seen, but I got this message in terminal:

** (gnome-panel:9383): WARNING **: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
(gnome-panel:9383): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.

And - cant log out. When I do a hard reboot the changes are gone, and the bottom of my monitor is again lonely for its panel.

Thanks!

FE

---

### Post by blazemore on 2009-11-08
Don't run that command in the terminal.

Hit alt + F2 and type it in the box that comes up.

Your panels will restore straight away, but make sure you log off and on again; it's something to do with permissions.

---

### Post by fisheater on 2009-11-09
Thank for the update - I ran it in alt+f2, it the panel appeared and switched me to 'root' in the name by the power button (top right).

After that I was unable to log out, exit, turn off my computer. I had to hard restart it with the button... The changes dont persist.

Suggestions?

Regards

FE

---

### Post by matthewbpt on 2009-11-09
Type the following in the terminal
```
rm -r ~/.gconf/apps/panel/
```

Then restart, your panel should be restored to default.

---

### Post by fisheater on 2009-11-10
[QUOTE=matthewbpt;8278610]Type the following in the terminal
```
rm -r ~/.gconf/apps/panel/
```

Thanks! That worked!

I am left with the problem of not being able to ALT+TAB between my open windows. I have checked the key binding (System>Preferences>Keyboard Shortcuts) - and it still is present just not working.

I also tried to rest my visual settings (changed from normal to none then back to normal) with no effect.

Then I change in configuration editor: apps>metacity>cycle windows to <alt>tab and still nothing. (idea from: [http://www.jessedyer.com/content/Ubuntu-Alt-Tab-stopped-working-fixed](http://www.jessedyer.com/content/Ubuntu-Alt-Tab-stopped-working-fixed))

This is the most useful key in my ADHD world! 

Summary: all fixed except alt-tab!

Thanks FE

---

### Post by blazemore on 2009-11-10
Are you using the Normal or above desktop effects?

If so, Compiz isn't getting your Alt+Tab properly.

Install the package "compizconfig-settings-manager", hit Alt+F2 and type "ccsm" Without the quotes.

When the settings manager pops up, scroll down to the bottom. There's a number of different window switchers, the one you're probably looking for is called "Static Application Switcher" (or similar, this is from memory) Make sure it's enabled.

---

### Post by fisheater on 2009-11-10
Thanks! That was it!

It was checked, and when I looked at the settings, the window switching was Ctrl+Alt+Tab. Not sure how that was changed, but I reset it to Alt+Tab and back in business. 

Now I am back to overheating my nervous system with too many windows open.

Thanks heaps. This is why ubuntu is great - good to start, superb help from all of you.

Please mark as resolved.

FE!

---

### Post by philinux on 2009-11-10
> **fisheater said:**
> Thanks! That was it!

It was checked, and when I looked at the settings, the window switching was Ctrl+Alt+Tab. Not sure how that was changed, but I reset it to Alt+Tab and back in business. 

Now I am back to overheating my nervous system with too many windows open.

Thanks heaps. This is why ubuntu is great - good to start, superb help from all of you.

Please mark as resolved.

FE!

You mark it solved yourself. Click the [COLOR="Red"]_**Thread Tools**_[/COLOR] button

---

### Post by fisheater on 2009-11-11
One last comment: This fully solved my issues:
[http://helpforlinux.blogspot.com/2009/08/restore-ubuntu-panels-back-to-their.html](http://helpforlinux.blogspot.com/2009/08/restore-ubuntu-panels-back-to-their.html)

From the webpage above:
Open the Terminal. 

Once the Terminal window opens, enter the following command at the prompt:
gconftool --recursive-unset /apps/panel 
(Remember: There should be no spaces between the two dashes before shutdown.)
Then enter the next command:
rm -rf ~/.gconf/apps/panel
And enter one more command:
pkill gnome-panel

Use at your own risk! (it worked for me)

Ty

---

### Post by bean@ on 2011-03-19
> **matthewbpt said:**
> Type the following in the terminal
```
rm -r ~/.gconf/apps/panel/
```Then restart, your panel should be restored to default.
  
your post helped me undo stupid mistake,thanks! As a new ubuntu convert these forums are invaluable in helping one learn and rectify errors.

---

