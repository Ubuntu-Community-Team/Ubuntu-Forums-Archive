---
title: "Uptime Notification Applet"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by for.i.am.root on 2010-04-15
Hi All:

So recently my wife has been yelling at me about how much time I spend on the computer. She likes to throw out these insane numbers like 8 hours or something, so I wrote this little script to display the current uptime in the notification area (it updates when you click on it). Just thought I would share. Let me know what you think.

You need to have imagemagick (to draw the uptime over the background image) and zenity (to create the notification icon) installed.

sudo apt-get -y install imagemagick zenity

Extract the archive to your home folder. Then run (you may have to chmod +x) the gnome-panel-uptime script.

See screenshot for preview.

Tech side:

It's a very simple script:

Export the current uptime.
Use sed to leave just the uptime and to trim whitespace.
Use ImageMagick's convert from the CLI to draw the uptime onto a background image.
Use Zenity to create the notification icon.
Have the function call itself so it will update when clicked.

PLEASE let me know what you think.

Thanks!

EDIT: So I found some bugs already :( If you add it to your .bashrc file when you first boot it does not display properly. It adds min after the uptime when the uptime is less than 59 minutes. It also does not display correctly when the uptime is greater than 9:59.

Will re-upload after fixed.

I am also adding a case statement to change the font based on the wc of the uptime. This way single digits will be easier to read and longer uptimes will display properly.

Thanks!

EDIT: So I integrated the above fixes, as well as an if statement to check for the presence of convert and zenity. It works much better now. Will let you know how well it works at uptimes of 10 hours and more.

---

### Post by for.i.am.root on 2010-04-16
Hi All:

At an uptime of 10:45 the font is small, however, still readable. I am working on one that will display in full size similar to the clock applet in the taskbar instead of the notification area.

Let me know what you think and please send bugs/problems and (or) fixes/solutions my way.

Thanks!

---

### Post by warfacegod on 2010-04-17
Brilliant idea! My wife tries to tell me I spend whole days on my laptop (it couldn't be more than .98 of a day:biggrin:).

---

### Post by for.i.am.root on 2010-04-20
Hi:

Mine's the same :) I'm pretty sure all "spouses'" are :) It doesn't work very well after 23:59. It only displays the first 5 characters or so "1 day". I am working (when I can) on an if statement to check if the day string is present and then convert it to hours (To be considered a "patch". After 4 days it wouldn't display properly (50 pixel max) without a tiny font.).

Will keep everybody updated on progress with a real taskbar applet instead of a "Notification Icon" :).

Thanks!

---

