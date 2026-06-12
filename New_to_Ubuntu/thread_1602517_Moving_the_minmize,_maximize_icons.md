---
title: "Moving the minmize, maximize icons"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by newport_j on 2010-10-21
I am using Ubuntu 10.04. When I open up the command line screen, the x _ and empty square are on the upper left corner. It should not be that way. I want them on the upper right hand corner. So how do I move them?
 
Newport_j

---

### Post by cstudent on 2010-10-21
Install [Ubuntu Twea]("http://ubuntu-tweak.com/")k. You can use it to switch the buttons and a whole lot of other things. Look under Applications > System Tools after installation.

---

### Post by trikster_x on 2010-10-21
If I remember right, you just have to open the appearance menu, and select a different theme.  I believe ambience is the only one with the buttons on the left.  If you like the ambience look, then select a different theme to get the buttons where you want them, then select customize, and change everything to ambience.

---

### Post by d5xtgr on 2010-10-21
Applications: System Tools: Configuration Editor
in the left pane, Apps: Metacity: general

in the right pane, modify the button_layout as desired

---

### Post by Megaptera on 2010-10-21
Guide with screenshots here:

[http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/](http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/)

---

### Post by trikster_x on 2010-10-21
> **d5xtgr said:**
> Applications: System Tools: Configuration Editor
in the left pane, Apps: Metacity: general

in the right pane, modify the button_layout as desired

Actually, the configuration editor is not available in the system tools menu on a fresh install.  You have to right click on the applications panel launcher, select edit menus, go to system tools, then check the box next to configuration editor to unhide it.

When you get to button_layout, move the colon to the left if you want the buttons on the right, move the colon to the right if you want the buttons on the left.

---

### Post by fatality_uk on 2010-10-21
Enter the following code into the terminal

> gconftool-2 --set /apps/metacity/general/button_layout --type string menu:close,minimize,maximize


---

### Post by d5xtgr on 2010-10-21
> **trikster_x said:**
> Actually, the configuration editor is not available in the system tools menu on a fresh install.  You have to right click on the applications panel launcher, select edit menus, go to system tools, then check the box next to configuration editor to unhide it.

When you get to button_layout, move the colon to the left if you want the buttons on the right, move the colon to the right if you want the buttons on the left.
Hm, I don't remember doing that...
Anyway, I found something related and would hate to think that we're all trashing gnome doing this, so:

> **[COLOR="DarkRed"]Minimize, Maximize and Close button placement.[/COLOR]**
A decision has been taken to move the placement to the left. Mark Shuttleworth explained that this was because "something" is going to be placed in the right hand area in the next release. Moving the buttons now would help enable this change.
**[Update ]**[http://www.markshuttleworth.com/archives/333](http://www.markshuttleworth.com/archives/333)

The buttons are in the old location on all default themes apart from Ambiance,Radiance and Dust, If you still want the Ambiance ,Radiance or Dust theme but with buttons on the right, choose one of those other themes and use the Customize button to achieve what you want. e.g.
1. System > Preferences > Appearance
2. Select the theme icon "New Wave"
3. Click the button "Customize.."
4. Select tab "Controls" and select "Ambiance"
5. Select tab "Window border" and select "Ambiance"
6. Select tab "Icons" and scroll down and select "Ubuntu-mono-dark"
7. Select "Save Theme" to your choice.
**Using gconf-editor is not the right approach as this could bork future themes. This change makes it easier for themes to do interesting things with window borders. Unfortunately, if the wrong approach spreads, they won't be able to do that.**

---

### Post by trikster_x on 2010-10-21
So for next release, I am assuming that means 11.04?  When was the article written?

---

### Post by d5xtgr on 2010-10-21
The blog post is dated May 3rd.  From what I read the feature is still in development and is called 'windicators'.  In any case, we should at least be aware that the gconf method may have unintended consequences.

---

