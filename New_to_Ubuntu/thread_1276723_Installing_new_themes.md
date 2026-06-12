---
title: "Installing new themes"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by seandude on 2009-09-27
I'm trying to install some new themes.  The first ones came from gnome-look, the others came from gnome art manager. For some reason it wont work. 

I was wondering if someone could just walk me through the steps of installing a new theme so I can see where I've gone wrong.

---

### Post by LoloftheRings on 2009-09-27
Download a .tar.gz from the internet, DO NOT UNPACK THEM, go to System -> Preferences -> Appearance, press the Install button and select your .tar.gz package.

There should be a tool for this, like in kde4.. Or at least a file format like emerald does (*.emerald) so you can just double click it..But there isn't.

---

### Post by aysiu on 2009-09-27
If it's a GTK or Metacity theme: [list=1][*]Download the theme. Do not click on the download or extract it. Just leave it as is.[*]Go to System > Preferences > Appearance. A new window will open. Keep it open.[*]Drag the downloaded theme to the Appearance window. Let go.[/list] If it's a GDM theme: [list=1][*]Download the theme. Do not extract it. Leave as is.[*]Go to System > Administration > Login Window[*]Click on **Local** and then **Add**. Find the theme file.[/list]

---

### Post by seandude on 2009-09-27
Lol; I've tried that and I get 

**There was an error installing the selected file**
[FONT=Arial] "Shiftie_Black_by_ebupof.gz" does not appear to be a valid theme.

aysiu; When I try adding it through the Login Window thing, it doesn't view compressed files, and when I try to change it to see them, it wont let me.
[/FONT]

---

### Post by aysiu on 2009-09-27
> **seandude said:**
> Lol; I've tried that and I get 

**There was an error installing the selected file**
[FONT=Arial] "Shiftie_Black_by_ebupof.gz" does not appear to be a valid theme.

aysiu; When I try adding it through the Login Window thing, it doesn't view compressed files, and when I try to change it to see them, it wont let me.
[/FONT]
The file name is messed up for some reason. Rename it to *Shiftie_Black_by_ebupof**.tar.gz*** and then try again.

---

### Post by seandude on 2009-09-27
Done.  For some reason though, it's telling me that the archive isnt a tar.gz file (it is though).

the exact error it's giving me is.


"Not a theme archive
File not a tar.gz or tar archive"

---

### Post by aysiu on 2009-09-27
That's weird. I just tried it with that exact theme.

Okay. Well, backup plan.

Right-click the file and select *Extract Here*.

If it gives you a file with a .tar extension, do it again with that new file until you get a folder.

Then paste that folder in the /home/*username*/.themes directory

The .themes directory is a hidden folder, so you have to press Control-H to see it.

---

### Post by seandude on 2009-09-27
Ok, so it has been moved to .themes.  Now what?  It hasn't appeared, and I'm not sure what I'm supposed to do now.

---

### Post by aysiu on 2009-09-27
> **seandude said:**
> Ok, so it has been moved to .themes.  Now what?  It hasn't appeared, and I'm not sure what I'm supposed to do now.
It won't appear as a main theme. You have to go to System > Preferences > Appearances, select *Customize* and then find the theme in Controls and in Window Border

---

### Post by seandude on 2009-09-27
PERFECT!!!!  Thank you, it's up and working fine now.  Two other questions though:

1.  When downloading from Gnome Art Manager, is the process for installing a new theme is theme the same?

2. What do I do if a control is GTK+

---

### Post by aysiu on 2009-09-27
Properly packaged themes should just be drag and drop to the Appearances window. It doesn't matter what site they come from.

---

