---
title: "I tried to reset my panels, but something screwed up..."
date: 2009-11-30
forum: New to Ubuntu
---

### Post by SPazzo on 2009-11-30
So I'm on my MSI Wind netbook with Ubuntu 9.04 installed.  (Plus a dual-boot with Windows XP).  A couple weeks ago I accidentally removed something from the top panel, I looked on the internet and found [some instructions]("http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html") on how to reset the panels to the default settings.  It worked fine.

Flash forward to about 10 minutes ago, I accidentally removed the network icon from my top panel, so I decided to use the same instructions to reset my panels.  It didn't work.  It got rid of the bottom panel, and now windows minimize to thetop panel.  Plus my Applications/Places/System buttons are gone.

Any ideas?

EDIT:  I fotgot to mention, I tried[ these instructions]("http://www.celsius1414.com/2006/08/31/how-to-reset-gnome-panel-to-default-in-ubuntugnome2") as well, and that just reset my theme to what the screenshot shows.

PS The screenshot is what it looks like now.

---

### Post by wesleybailey on 2009-11-30
I'm not sure how to reset things, but here are the steps to get your bottom panel back.

1. Right-click on your panel, click "new panel"
2. If the panel is showing up on the left or right of the screen, right click on the new panel, and press properties, change the orientation to bottom. 
3. To have your minimize windows show up on the bottom panel, right click on the bottom panel, and click "Add to Panel"
4. Choose "Window List", and click Add
5. If there is anything else missing from the bottom, panel just repeat step  3, and add the next item.

Hope this helps

---

### Post by wojox on 2009-11-30
CTRL + ALT + F1

```
sudo rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

```
sudo reboot
```

Log back in.

---

### Post by SPazzo on 2009-11-30
I tried wojox's post and it didn't do anything.  wesleybailey's won't work because no matter where I click on the panel, it doesn't say anything about add new panel.  Even if I click preferences it doesn't go to what it showed before.

---

### Post by wesleybailey on 2009-11-30
If you right-click on the panel close to an icon, then it won't give you a "New Panel" option. You need to right-click, on an empty spot in the middle of the panel.

If you don't get "New Panel" option, what options do you get when you right-click the menu?

---

### Post by SPazzo on 2009-11-30
OK, so I tried right-clicking and clicking on remove from panel.  There was something on there that was blocking the Add New Panel dialogue.  So I added a new panel, and started restoring my old panels, but now I think I messed up the desktop.  For one, if I open any kind of Window it doesn't have a bar at the bottom.  And the Close/Minimize/Maximize buttons hide behind the top panel.  AND if I right-click on my desktop nothing comes up!

ARRRGH!!!

---

### Post by wesleybailey on 2009-11-30
Try logging out, and logging back in. There is no reason you should not be able to right click on your desktop.

Is this a fresh install, or have you been using this desktop for awhile.

One way to reset all of the settings, is to delete/rename your .gnome2 folder. However that will get rid of any customization you have done.

If you go this route, I recommend renaming the directory, in case something goes wrong.

From terminal

mv ~/.gnome2 ~/.gnome2-back

Then log-out and log back in.

---

### Post by SPazzo on 2009-11-30
It's a fresh install from about 2 weeks ago.

Anyway, I tried renaming the Gnome2 folder.  Didn't work.  Tried deleting it and deleting the backup (gnome2-back).  Didn't work.  And yes I did log out and log back in.

---

### Post by wojox on 2009-11-30
Okay open you terminal and reinstall gnome-panel

```
sudo apt-get --reinstall install gnome-panel-
```

Then 

```
sudo killall gnome-panel
```

---

### Post by wesleybailey on 2009-11-30
wojox idea will reset the panel

This will completly reset all gnome settings, did your right click start working again?

From a terminal,deleting these hidden folders will give you the default configuration after login out and then in

```
rm -r gnome2* gconf gconfd
```

---

### Post by SPazzo on 2009-11-30
wojox:  That completely removed both panels.  The right click won't work, and neither will ALT-F2 to bring up open application.

I tried CTRL-ALT-F2 and then sudo reboot, when I logged back in, the same thing.  This really sucks.

---

### Post by SPazzo on 2009-11-30
wesleybailey:  I tried your idea on CTRL-ALT-F2 and I just got a message saying cannot delete, no such file or folder.

It looks like I'll just have to reinstall.  I don't think I had too much stuff I can't get back.

---

### Post by SPazzo on 2009-11-30
I'm going to do a clean install.  Unless anyone has any other ideas?

---

### Post by wesleybailey on 2009-11-30
Did you try deleting those directories, and logging out an logging back in?

---

### Post by SPazzo on 2009-11-30
Yep, but I did that after I did wojox said.  What wojox said seems to have killed everything.  I can't open anything at all.

---

### Post by wesleybailey on 2009-11-30
Try deleting those directories again.

Open a termial:

Press Alt-F2(run dialog), and type gnome-terminal.

In the terminal delete those directories again.

Instead of re-installing completely you could create a new user, and that would have all the default settings.

---

### Post by SPazzo on 2009-11-30
I would love to, but if I try ALT-F2, nothing happens.  If I try CTRL-ALT-F2, and then deleting those folders, it says *cannot remove no such file or directory.*

It seems that the desktop is just gone.  Is there a way to reinstall the desktop from tty2?

---

### Post by wesleybailey on 2009-11-30
This will install the desktop
sudo apt-get install ubuntu-desktop

However I don't think its gone, just the settings are messed up.

Try deleting the user, and then adding it back
sudo userdel -r <username>

sudo useradd  <username>

---

### Post by SPazzo on 2009-11-30
Well, before I did that I just added a new user.  When i booted into that user it was on Ubuntu Netbook Remix.  I had installed that before, but I didn't like it so I changed back to the normal desktop, but kept it installed.

What I was at was Ubuntu Netbook remix, without the netbook remix window up.  Weird huh?

So I'll just backup everything on my old user from this user and just use this user.  Thanks for all the help!

---

### Post by wesleybailey on 2009-11-30
Awesome, I'm glad to hear it's working again, it sure beats re-installing ubuntu completely.

Please mark this thread as solved.

---

