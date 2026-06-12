---
title: "Accidentally deleted my desktops from the panel."
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Kajika on 2009-01-12
[COLOR="Red"]EDIT![/COLOR]Everything below in blue is fixed, but I still can't get the Compiz 3d cube to work. I've done it before & it WAS working, but now I have no 3d effects whatsoever. Read my other posts for more details, please help this lost newbie, & thank you for the support!


[COLOR="RoyalBlue"]I'm brand SPANKING new from XP, so please assume I'm clueless & everything is more or less on the default setting. I was poking around with the 3d cube desktop function in compiz & had everything where I wanted it. Then, in a moment of blind curiosity, I right-clicked on the mini-windows in the bottom-right of the bottom-screen panel & clicked something that deleted them. I can't find a way to get them back, I restarted out of frustration, & now none of the 3d/compiz effects are working. I went into compiz & everything is just how I left it, but for some reason is not working. When I hit ctrl+alt+left, right, or down it brings up a little window giving me the option to switch desktops.[/COLOR] I just want to get that window back onto the panel & to get my 3d effects up & working once again. Thanks!

---

### Post by ibuclaw on 2009-01-12
Do you still have the top panel on your desktop?

If so, you should be able to recreate the bottom one by right-clicking on it and selecting New Panel

Regards
Iain

---

### Post by Kajika on 2009-01-12
Yep, I've got the top one still, but under Properties I don't see anything that would restore the panel, just options to change the colors, etc.

---

### Post by Kajika on 2009-01-12
Ah, sorry, I didn't read your post close enough. I just gave that a try though, but it didn't work. It just gave me a blank panel. I've tried going into 'add to panel' but I don't see it as an option in there.

---

### Post by Kajika on 2009-01-12
Just giving this a quick bump. I'm sure this is something ridiculously simple to everyone else, but I can't find an answer anywhere!

---

### Post by ChildOfMana on 2009-01-12
I think you're looking for 'Workspace Switcher' (if I've read your post right).

There should be an entry for it in the 'Add To Panel' menu.

Right-click on the panel, select 'Add To Panel' and scroll down until you find it - it should be near the bottom. Then highlight it and click 'Add' and just move it to where you want it on the panel.

Edit: you can also rotate your desktop cube (and thus switch workspaces) by holding Ctrl + Alt + Left Mouse Button.

---

### Post by Kajika on 2009-01-12
Thank you so much! I just had no idea what it was called. That fixed that. 
I still can't get to my cube, though. I had it working for a while, but even ctrl+alt +right click won't bring it up.

---

### Post by kapok on 2009-01-12
right click bottom panel.
there is an 'add to panel' option.
click this and scroll down the list.
near bottom is a 'workspace switcher'.
click it and than hit add at the bottom of that window.

if you go to applications -> add/remove there is a compiz fusion icon application, which puts a little icon of what you're already using in the corner of you're screen. from there you can edit preferences concerning window effects, and there is an option which reloads the window manager. this is you're best bet if you're trying to control the window effects and get them working.

and also, welcome to ubuntu. :)

---

### Post by kapok on 2009-01-12
the cube options are located in the preferences section of above said app.

---

### Post by ChildOfMana on 2009-01-12
You're welcome.

Now let's see about your desktop cube. Have you got Compiz Config Settings Manager installed?

If not open a Terminal (Applications > Accessories > Terminal) and type the following;

> sudo apt-get install compizconfig-settings-manager

Once installed you should find it in System > Preferences. Open it up and select 'Desktop' from the left-hand menu. Now ensure there is a tick next to 'Desktop Cube' *and* 'Rotate Cube'. Also go to 'General' in the left-hand menu then click on 'General Options' and go to the 'Desktop Size' tab. Set the value for 'Horizontal Vertical Size' to 4 (or more) and you should now have a desktop cube.

---

### Post by Fielder on 2009-01-12
Hi, You know I did the same thing,and redid the hole thing over. :(

---

### Post by Kajika on 2009-01-12
> **ChildOfMana said:**
> You're welcome.

Now let's see about your desktop cube. Have you got Compiz Config Settings Manager installed?

If not open a Terminal (Applications > Accessories > Terminal) and type the following;



Once installed you should find it in System > Preferences. Open it up and select 'Desktop' from the left-hand menu. Now ensure there is a tick next to 'Desktop Cube' *and* 'Rotate Cube'. Also go to 'General' in the left-hand menu then click on 'General Options' and go to the 'Desktop Size' tab. Set the value for 'Horizontal Vertical Size' to 4 (or more) and you should now have a desktop cube.
Yes to all of that. I had it all beautiful & running until I deleted the workspace switcher. The cube, & all of my 3d effects haven't worked since then. 
I've tried completely uninstalling & reinstalling Compiz completely then re-doing everything (desktop cube, rotate cube, 4 windows, etc.) but it doesn't make a difference. ctrl+alt+ up, down, & side all give me the option to switch desktops but with no effects. ctrl+alt+left click does nothing (on the desk top it just drags around the selection box).

---

### Post by Kajika on 2009-01-12
I'm bumping this because I just edited the first post to reflect the  issue at hand. I'm currently having trouble with my Compiz 3d cube, please read my other posts, & ask if you need more details. Thank you!

---

### Post by ibuclaw on 2009-01-12
Can you verify that compiz is definately running?

To make sure it is, press **Alt+F2** to open the Run Command Dialogue and type in:
```
compiz --replace
```

Regards
Iain

---

### Post by Kajika on 2009-01-12
Here's what I got when I ran it in the terminal (running it the regular way didn't do anything). This is only my 3rd day with Ubuntu, so I really don't know what this means, sorry.

Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x768) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by Kajika on 2009-01-12
And like magic it's working again! For whatever reason, I hit ctrl+alt+ left click, & it's working! Thanks for all the help everyone!

---

### Post by ibuclaw on 2009-01-12
> **Kajika said:**
> Here's what I got when I ran it in the terminal (running it the regular way didn't do anything). This is only my 3rd day with Ubuntu, so I really don't know what this means, sorry.

Checking for Xgl: not present. 
Detected PCI ID for VGA: 
[B]Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x768) to maximum 3D texture size (4096): Passed.[/B]
Checking for Software Rasterizer: Not present. 
[B]Checking for nVidia: present. 
Checking for FBConfig: present. [/B]
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

That should be fine then, NVIDIA is detected, and so is composition support.

Do you have ccsm installed?
```
sudo apt-get install compizconfig-settings-manager
```

Then go into **System->Preferences->Advanced Desktop Effects**

Click on **General Options** then on the **Desktop Size** tab, and ensure that the **Horizontal Virtual Size** is equal to 4 (or whatever number you chose it to be).
Given that is correct, click **Back**.

On the Left Panel under **Category**, click **Desktop** and the viewable settings will be filtered to just the Desktop ones.
Ensure that **Desktop Cube** is checked, and **Rotate Cube** is checked also.

Now try rotating the desktop cube (or **spin the cube**, as some have come to call it).

And let us know if you encounter any problems.

Regards
Iain

---

### Post by ibuclaw on 2009-01-12
> **Kajika said:**
> And like magic it's working again! For whatever reason, I hit ctrl+alt+ left click, & it's working! Thanks for all the help everyone!

Ah, good good :)

You might want to ensure that compiz is loaded everytime you login then.

Press **Alt+F2** and enter in:
```
gconf-editor
```
And enter the key directories:
**desktop -> gnome -> applications -> window_manager**

And set the **current** and **default** key to:
```
/usr/bin/compiz
```

Also, I would like to make a note, that you may want to consider [ubuntu-tweak]("http://ubuntu-tweak.com/downloads") as an application you'll want. It makes some basic setup tasks in ubuntu very easy indeed for the new user.

It even allows you to completely lockdown the panels, so you don't accidentally delete them again.


Regards
Iain

---

### Post by bro brian on 2009-10-21
I had the same problem (or similar). I did something to delete my 2 desktop squares in the lower panel. I followed the advice (given previously), and was able to get them back.
 My problem I had then was - when I clicked on the right hand desktop square, there was no upper nor lower panels, and right clicking the desktop did nothing. I had to manually shut off the laptop to get out of it.
  I still had the compizconfig settings manager, and (under options) it showed that the number of desktops I had were 2.

  Must have been some sort of glitch in the computer because - I had earlier installed a "compiz fusion icon" in the upper panel, and when I switched back from compiz to metacity, I had the upper & lower panels back in the other desktop. I switched back from metacity to compiz, and everything worked again. Granted I had to reset my options in the compiz settings manager again.

---

### Post by nijibug on 2010-09-28
> **ChildOfMana said:**
> I think you're looking for 'Workspace Switcher' (if I've read your post right).

There should be an entry for it in the 'Add To Panel' menu.

Right-click on the panel, select 'Add To Panel' and scroll down until you find it - it should be near the bottom. Then highlight it and click 'Add' and just move it to where you want it on the panel.

Edit: you can also rotate your desktop cube (and thus switch workspaces) by holding Ctrl + Alt + Left Mouse Button.

Thank you so much for this! I had no idea they were called 'Workspace Switcher' and that was the only thing keeping me from finding them again. This solved my problem.

---

