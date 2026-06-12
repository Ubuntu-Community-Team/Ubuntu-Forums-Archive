---
title: "moving an icon from the desktop into the applications menu"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by naomibrown on 2010-01-06
Hi,

I'm using Ubuntu 9.10. 

I've just downloaded Scratch [http://info.scratch.mit.edu/Linux_installer]("http://info.scratch.mit.edu/Linux_installer") using the commands at the bottom of the page. 

I know I've not done it using the software centre, because I couldn't get it to find Scratch, but is there a way to put it in Applications-Programming anyhow? The icon is currently on my desktop. 

Thanks!
Naomi

---

### Post by audiomick on 2010-01-06
right click on applications
choose new entry
search for the thing you want it to point at.

---

### Post by Anuovis on 2010-01-06
You can edit most of the menu entries.
*Right click on *Applications>Edit Menus*
or
*Go to *System>Preferences>Main Menu*

From there you might already see the desired entry somewhere else or unchecked, just enable it and drag where you want it to be. Or you can add *New Item *for that new app.

---

### Post by naomibrown on 2010-01-06
Hi,

Thanks for your replies. I've managed to move the icon into Applications now, but it doesn't run the program like clicking on the link on the desktop does, instead it launches a perl script.

Then I was stuck for a bit.

Then I looked in the perl script and decided that I needed to open up the same link as the perl script, not just the desktop icon.

This is what I have now in Properties when I click on Edit Menus then Scratch. 

Type: Application
Name: Scratch
Command: /home/naomi/Scratch/runscratch.sh
Comment: none

---

### Post by Anuovis on 2010-01-06
If you ever need a _*Command*_ for running something, you can check the desktop, menu or panel icon of that app. Somewhere in the properties it will have it, you can then type it into the terminal or create shortcuts and menu entries here and there. Quite convenient.

---

