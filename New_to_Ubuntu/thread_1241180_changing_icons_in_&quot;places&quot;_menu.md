---
title: "changing icons in &quot;places&quot; menu"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by thomz92 on 2009-08-15
hi

i just downloaded and installed an icon theme but it failed to change the icons for my music, pictures, etc folders in the places menu at the top of the screen. is there any way i can change this? i tried the menu editor but for some reason it doesn't include the places menu, only the applications and system menu. 

thanks

---

### Post by fooman on 2009-08-15
what theme and how did you install the theme?  usually all it takes to install is to open the appearance preferences box (system > preferences > appearance),  then drag & drop the .tar.gz file into the preferences window.

also,  have you tried logging out and back in again?...that might do it.

---

### Post by thomz92 on 2009-08-15
icon set: [http://www.gnome-look.org/content/show.php/black-white+2+Gloss?content=72621](http://www.gnome-look.org/content/show.php/black-white+2+Gloss?content=72621)

i unzipped everything until i got a folder, and then i dragged n dropped that into the appearance window. all the icons work accept the ones in the places menu. i guess they defaulted to an ugly gnome style and it doesn't match at all. anyway, i really want to change them.

---

### Post by fooman on 2009-08-15
i use that same theme!  :)

try it the way i described above....there is no need to unzip themes/icons/mouse cursors....just drag and drop the unzipped .tar.gz file into the appearance preferences window and you should be good.

---

### Post by thomz92 on 2009-08-15
do you have the same problem? anyway, why would keeping it zipped help? doesn't it unzip it anyway? and it said it installed fine and asked me if i wanted to apply the new theme now...

---

### Post by fooman on 2009-08-15
no i do not have same problem.

why?  ...sorry, i do not know, but i do know that *not* unzipping it first is the correct way.

anyways,  i did make a mistake...the file you downloaded is a .tar file (i think)...so you do need to unzip it once.  that will create another folder which will contain a .tar.gz file and yet another folder.

it is that .tar.gz file that you need to drag and drop, *not* the folder it produces!

---

### Post by Fzang on 2009-08-15
Music, Documents, Pictures, Videos directories are not treated as "special" directories by the theming system, so they will just get skinned with a normal folder icon. In the next version of Ubuntu they're becoming more special and individual and will be themed by icons.

...If this is what you meant? Could you post a screenie if it wasn't?

---

### Post by thomz92 on 2009-08-15
srry fooman it didn't work. [IMG]/home/thomas/Desktop/Screenshot.png[/IMG]

---

### Post by thomz92 on 2009-08-15
uh i dont think that screenshot worked. how do u post screenshots?

---

### Post by wojox on 2009-08-15
Apparently straight off the Desktop. :lolflag: :lolflag: :lolflag:

---

### Post by thomz92 on 2009-08-15
hey no mocking noobs :)

---

### Post by wojox on 2009-08-15
Look in your Control Panel for Pictures and Albums and upload you picture from there. Click Add Album name it and upload.

---

### Post by theozzlives on 2009-08-15
I tried it. You unzip the .tar file, then inside the folder is a .tar.gz file. You drag that into themes and it'll work. My places are changed.

---

### Post by thomz92 on 2009-08-15
well anyway i dont need a screenshot. i downloaded it, untarred it, dragged the .tar.gz file, it installed, but the places aren't changed... im using 9.04...would that make a difference?

---

### Post by fooman on 2009-08-15
i am using 9.04

may have to do with the way you did it in the first place.  try undoing what you did before first,  then try dragging the tar.gz into the appearance window....see if it makes a difference.  try this:

open your home folder (places > home folder),  click on "view" in the toolbar and put a check next to "show hidden files".  find the .icons folder and open it.  inside you should see a folder called "black-white_2-style" (or similar)....right-click on it and choose "move to trash".  

log-out and back in again.

open the appearance preferences window again and drag and drop the .tar.gz file into it.... see if it works.

good luck.

---

