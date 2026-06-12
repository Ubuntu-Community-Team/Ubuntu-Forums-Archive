---
title: "gnome shell niggle... ..."
date: 2010-02-17
forum: New to Ubuntu
---

### Post by techno-mole on 2010-02-17
hello, me again.

does anyone know how to change the time in gnome shell from am/pm to 24 hour ? I believe you can edit one of the js files, but I have no idea what to edit to, I also found a patch but there was no hint as to how to apply it.

its a small thing, and I know gnome shell is still being tested etc, but I would appreciate a hint, you would think this would be an easy thing to do, eg - right click on the clock and select options, and then adjust accordingly.

cheers

---

### Post by -kg- on 2010-02-17
Yep, piece of cake!

Right click on the Date and Time applet and select "Preferences."  Right there on the "General" tab will be two radio buttons, one for 12 hour and one for 24 hour.  You know what to do from there.

---

### Post by techno-mole on 2010-02-17
cheers, but that isnt working, right clicking on the time applet doesnt do anything, i know thats how you do it when running gnome panels, but im not, im running gnome shell, and from what i can gather the only way to change the time (am/pm or 24 hour) is to edit one of the .js files that deals with the clock on the panel.

My javascript is bad to say the least, so i thought id ask for some help so i dont mess things up.

---

### Post by techno-mole on 2010-02-17
okay figured it out.

i had to open a file in a text editor, the file is found in - usr/share/gnome-shell/js/ui and its called panel.js

open this in gedit, or text editor of your choice (its best to use one that will show line numbers) you will either have to run gedit as root or copy the file to your home folder to edit it (thats what i did)

look for this line - ```
this._clock.set_text(displayDate.toLocaleFormat(_("%a / %d %B / %Y - %R")));
``` it should be about line 563 (hence the use of line numbers in the text editor)

now the line above is what i changed my file to, and from what i can figure out %a = day then /= this is just a separator, you can use hyphens etc 

then this part %d %B = the current date and again /=another separator 

and then %Y= the current year and in my file i used a - to separate the time from the date

and finally this part %R = 24 hour mode.

so in gnome shell on my system in the middle of the panel my time/date info reads like this ```
Wed / 17 February / 2010 - 22:38 
``` im not sure whether i will keep it like this, but i have the 24 hour clock now, so im happy, i prefer using a 24 time set up (i find it easier to figure out where i am in the day)

it would be better to have the clock on the top panel in gnome shell configurable in an easier way, eg - right clicking on it to show a menu and then various options for adjusting, im using a fairly up to date version of gnome shell (which i quite like actually) and the clock as yet had no configuration menu.

cheers, and hope this helps some one

---

