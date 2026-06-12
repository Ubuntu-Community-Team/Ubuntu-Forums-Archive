---
title: "Desk Top"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by thomasneilson on 2009-10-26
I've got 9.04. I wonder into a different desktop, looking much like an XP desktop. How does one get back GNOME desktop?
 
Tom :confused:

---

### Post by Rayve on 2009-10-26
You mean having changed the desktop appearance via System > Preferences > Appearance, or from right-clicking the top bar and choosing "Edit Menus"?  I believe you can "revert" menu changes made through Edit Menu, and you can choose a different layout through Appearance.

Or are you having a different issue?

---

### Post by thomasneilson on 2009-10-26
> **Rayve said:**
> You mean having changed the desktop appearance via System > Preferences > Appearance, or from right-clicking the top bar and choosing "Edit Menus"? I believe you can "revert" menu changes made through Edit Menu, and you can choose a different layout through Appearance.
 
Or are you having a different issue?
 
 
I don't think that is my problem.  What I have is a brown background with launchers that I generated.  I don't see any way to change back to the original desktop that I had.  
 
That desktop had options down eack side of the window.  
 
Tom

---

### Post by konqueror7 on 2009-10-26
you probably installed kubuntu? if you have gnome installed, logout and select 'Options' and select the 'GNOME Session', this will load your gnome desktop when you login. or, if you don't have the gnome desktop, open a terminal and issue the following command,

```
sudo apt-get install ubuntu-desktop
```

and proceed with loggin out and selecting your session. hope it helped.

---

### Post by thomasneilson on 2009-10-26
> **konqueror7 said:**
> you probably installed kubuntu? if you have gnome installed, logout and select 'Options' and select the 'GNOME Session', this will load your gnome desktop when you login. or, if you don't have the gnome desktop, open a terminal and issue the following command,
 
```
sudo apt-get install ubuntu-desktop
```
 
and proceed with loggin out and selecting your session. hope it helped.
 
 
This is part of my problem.  I don't see any way to log out of current session.  I push the on-off switch and get  the option to turn off, restart, suspend or hibernate.  Nothing about logging off.  I've used Microsoft Windows so long, I really feel stupid.  Sorry.
 
Tom

---

### Post by Rayve on 2009-10-26
In the right-hand corner, do you see a red (power button) icon with your username beside it?  If you click on your name, you should see a drop-down menu, and one of those options should be "Log out...".

I'm sure there is a way to go to Applications > Terminal and do this from the command line, especially if kubuntu is very different from Ubuntu, but I'm afraid I don't know it.

---

### Post by sandyd on 2009-10-26
gnome-session-save --kill

---

### Post by thomasneilson on 2009-10-26
> **Rayve said:**
> In the right-hand corner, do you see a red (power button) icon with your username beside it? If you click on your name, you should see a drop-down menu, and one of those options should be "Log out...".
 
I'm sure there is a way to go to Applications > Terminal and do this from the command line, especially if kubuntu is very different from Ubuntu, but I'm afraid I don't know it.
 
 
I don't have a power on the desk top, anywhere.  I've pressed alt-f2, nothing.  I don't see how to log off or go to applications.

---

### Post by thomasneilson on 2009-10-26
> **carlee said:**
> gnome-session-save --kill
 
 
I don't know what you are telling me.

---

### Post by Rayve on 2009-10-26
The code ```
 gnome-session-save --kill 
``` that carlee supplied should be entered into a terminal... which you should be able to get to by pressing Alt+F2 and typing "gnome-terminal" in the window that appears, or selecting Applications > Terminal.

If you don't see those things, I'm not exactly sure what it is.  Can you perhaps submit a screenshot?  If you press the "Print Screen" (perhaps Prt Scr on some keyboards), do you then get an option of where to save the .jpg?  If so, save it to your desktop or somewhere currently easy for you to find, and then post it here.  Perhaps if we can see what you are, we can be of more assistance.

---

### Post by thomasneilson on 2009-10-26
> **Rayve said:**
> The code ```
 gnome-session-save --kill 
``` that carlee supplied should be entered into a terminal... which you should be able to get to by pressing Alt+F2 and typing "gnome-terminal" in the window that appears, or selecting Applications > Terminal.
 
If you don't see those things, I'm not exactly sure what it is. Can you perhaps submit a screenshot? If you press the "Print Screen" (perhaps Prt Scr on some keyboards), do you then get an option of where to save the .jpg? If so, save it to your desktop or somewhere currently easy for you to find, and then post it here. Perhaps if we can see what you are, we can be of more assistance.
 
 
F2 does nothing.  Perhaps if I can have your email address, I can send you a picture of my current desktop.  Thanks

---

### Post by The Real Dave on 2009-10-26
> **thomasneilson said:**
> F2 does nothing.  Perhaps if I can have your email address, I can send you a picture of my current desktop.  Thanks

Im presuming that this problem isn't persistant after a reboot, seeing as you seem to be having troubles getting out :) 

Press Ctrl + F1, you'll get a white text on black dialogue. Enter your login details (you won't be able to see your password, but it'll be going in), then type in 

```
sudo reboot
```

Give your password again, and your computer will reboot.

Hopefully, next time you login, your panels and that will have started up again.

---

### Post by thomasneilson on 2009-10-26
> **The Real Dave said:**
> Im presuming that this problem isn't persistant after a reboot, seeing as you seem to be having troubles getting out :) 
 
Press Ctrl + F1, you'll get a white text on black dialogue. Enter your login details (you won't be able to see your password, but it'll be going in), then type in 
 
```
sudo reboot
```
 
Give your password again, and your computer will reboot.
 
Hopefully, next time you login, your panels and that will have started up again.
 
 
Just so we are on the same song sheet, this desk top that I have is one that I was able
to get by using a drop down menue.  Can't remember which one.  I don't think I could get to it anyway.  This desktop seems to be an option to the OS.  I didn't mean to imply that there is a problem with the system.  Just a problem with my head.
 
Tom

---

### Post by The Real Dave on 2009-10-26
> **thomasneilson said:**
> Just so we are on the same song sheet, this desk top that I have is one that I was able
to get by using a drop down menue.  Can't remember which one.  I don't think I could get to it anyway.  This desktop seems to be an option to the OS.  I didn't mean to imply that there is a problem with the system.  Just a problem with my head.
 
Tom

Ah ok. Is it something you selected from the options menu on the login screen, or when you were actually in your desktop?

---

### Post by thomasneilson on 2009-10-26
> **The Real Dave said:**
> Ah ok. Is it something you selected from the options menu on the login screen, or when you were actually in your desktop?
 
 
It was when I was on the default desktop (GNOME).  I thought I would try the option and see if was faster.  It is faster but I want to go back but can't remember how.  It is hell to get old.
 
Tom  :(

---

### Post by SunnyRabbiera on 2009-10-26
did you install a XP theme or something?
Can you tell us what you did?

---

### Post by thomasneilson on 2009-10-26
> **SunnyRabbiera said:**
> did you install a XP theme or something?
Can you tell us what you did?
 
 
I don't remember anything about XP theme.  I do remember that it was called "Desktop" and a download folder was the only folder in the window.  Since I have created several launchers for that same window.  
 
I know when I go to the file browser, the folder desktop has the same files in it.  Maybe what I seeing is not a desktop but I know this window is what computer boots to.
 
Tom

---

### Post by fooman on 2009-10-26
right-click on panel and choose "add to panel" from the drop-down menu.

find "logout" in the list.  click once on it and then click "add" at the bottom.

you should now have a button that when pressed,  gives the options to "logout" and "switch user"

---

### Post by thomasneilson on 2009-10-26
> **fooman said:**
> right-click on panel and choose "add to panel" from the drop-down menu.
 
find "logout" in the list. click once on it and then click "add" at the bottom.
 
you should now have a button that when pressed, gives the options to "logout" and "switch user"
------------------------------------
 
 
 
When I right click on the panel, I get a pull down menue with these options
 
    Create folder
    Create Launcher
    Create Document
    Clean Up by Name
    Keep Aligned
    Paste (grayed out)
    Change Desktop Background
 
 
I see nothing about "add"
 
 
 
Tom

---

### Post by ricardopresto on 2009-10-26
Hi Tom

Are you using Ubuntu Netbook Remix?

richard

---

### Post by thomasneilson on 2009-10-26
> **ricardopresto said:**
> Hi Tom
 
Are you using Ubuntu Netbook Remix?
 
richard
----------------------------------
 
Yes, I am

---

### Post by ricardopresto on 2009-10-26
> **thomasneilson said:**
> ----------------------------------
 
Yes, I am


Right then...

Click on 'System' on the panel, then 'Preferences', then 'Startup Applications'. Scroll down the list to 'Netbook Launcher' and check the box. Reboot.

richard

---

### Post by thomasneilson on 2009-10-26
> **ricardopresto said:**
> Right then...
 
Click on 'System' on the panel, then 'Preferences', then 'Startup Applications'. Scroll down the list to 'Netbook Launcher' and check the box. Reboot.
 
richard
 
I don't think I'm able to make myself clear.  I don't have that option on my current desktop or drop down panel or anything else.  
 
Would it be easier to send you picture of my current desktop?
 
Tom

---

### Post by ricardopresto on 2009-10-26
> **thomasneilson said:**
> I don't think I'm able to make myself clear.  I don't have that option on my current desktop or drop down panel or anything else.  
 
Would it be easier to send you picture of my current desktop?
 
Tom

Do you have a panel on the desktop at all? (a bar across the top or bottom of the screen)

---

### Post by thomasneilson on 2009-10-26
> **ricardopresto said:**
> Do you have a panel on the desktop at all? (a bar across the top or bottom of the screen)
 --------------------------------
 
No, no panel at top or bottom or side.  I think the window is just showing what is my desktop folder.
 
Tom

---

### Post by ricardopresto on 2009-10-26
> **thomasneilson said:**
> --------------------------------
 
No, no panel at top or bottom or side.  I think the window is just showing what is my desktop folder.
 
Tom

Ok. Press Alt-F2. Scroll down the list to 'Panel' and click 'Run'

---

### Post by thomasneilson on 2009-10-26
> **ricardopresto said:**
> Ok. Press Alt-F2. Scroll down the list to 'Panel' and click 'Run'
 -------------------------
 
Nothing happens when I press Alt+F2

---

### Post by ricardopresto on 2009-10-26
> **thomasneilson said:**
> -------------------------
 
Nothing happens when I press Alt+F2

Ok, then try this.

Right-click on desktop. Select 'Create Launcher'. Make sure 'Application' is selected. Type a name - any name - in the next box, then click 'Browse'. Go to usr/bin/gnome-panel. This should create an icon on the desktop to create a panel. Once you have a panel, right-click on it and select 'Main Menu' from the list.

If this doesn't work I'm all out of ideas...

richard

---

### Post by thomasneilson on 2009-10-26
> **ricardopresto said:**
> Ok, then try this.
 
Right-click on desktop. Select 'Create Launcher'. Make sure 'Application' is selected. Type a name - any name - in the next box, then click 'Browse'. Go to usr/bin/gnome-panel. This should create an icon on the desktop to create a panel. Once you have a panel, right-click on it and select 'Main Menu' from the list.
 
If this doesn't work I'm all out of ideas...
 
richard
-------------------------------
Well, now I do have a tool bar at the top and the bottom.  With something to work with, I might be able to get back the orginal desktop.  Thanks lots
 
 
 
Tom   :D

---

### Post by thomasneilson on 2009-10-26
> **thomasneilson said:**
> -------------------------------
Well, now I do have a tool bar at the top and the bottom. With something to work with, I might be able to get back the orginal desktop. Thanks lots
 
 
 
Tom :D
---------------------------------------
 
Just some follow-up on where I was at.  
 
In the "system" pull down > preferences > Switch Desktop Mode > Ubuntu Netbook Desktop or Classic Desktop
 
Classic Desktop is the default Ubuntu desktop.
 
 
Thanks all for your help.

---

