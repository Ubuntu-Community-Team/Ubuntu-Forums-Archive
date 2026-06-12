---
title: "question about wallpapers"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by gnarlygnarlingtons on 2011-03-22
I kind of ****** up the wallpaper that I liked the most, cosmos. I was fooling around with the different wallpapers and set it as cosmos, which I liked a lot, but I wanted to change it to something else just to see it so I hit the "remove" button, thinking it meant remove as desktop background. What it actually did was remove it from the list altogether. Now I found the folder again and added it back to the list of backgrounds, but when I did it added them as individual pictures rather than as the complete slideshow that it was before. I know it is silly but I want my cosmos slideshow back like it was before. I cant find it on gnome or anywhere. Is this fixable?

---

### Post by robsoles on 2011-03-22
When you want to 'add' a dynamic wallpaper to the list you need to change from 'pictures' to 'all files' and then look for the .xml file accompanying the picture set and select it as what to add.

Any good?

---

### Post by gnarlygnarlingtons on 2011-03-22
I didn't see any .xml files. There was a folder called "cosmos" which contained .jpg files and when I added it to the backgrounds menu it just added all the individual .jpgs instead of the slideshow.

---

### Post by cymbaline42 on 2011-03-22
Here's your solution:


[LIST=1]
[*]Put all the 'Cosmos wallpapers' into a folder and save them wherever you want.
[*]Download and install this handy XML slideshow creator from here: [http://gtk-apps.org/content/show.php/XML+slideshow+creator?content=119728](http://gtk-apps.org/content/show.php/XML+slideshow+creator?content=119728)
[*]Open the XML slideshow creator, point it to the directory where you have stored the wallpapers use it to create your custom .xml file for those files.  You can also specify slideshow time (i.e. how frequently they will change automatically).   Choose 'Apply as background after generating'.
[*]Close the software, go to your desktop and you will see the cosmos dynamic wallpaper up and running again!
[/LIST]

---

### Post by robsoles on 2011-03-22
> **gnarlygnarlingtons said:**
> I didn't see any .xml files. There was a folder called "cosmos" which contained .jpg files and when I added it to the backgrounds menu it just added all the individual .jpgs instead of the slideshow.

So you are saying that in the dialog box/window in which you chose the 'cosmos' folder there wasn't a dropdown box with 'pictures' and 'all files' as choices?

If you can't see the .xml file that is with the pictures then you either aren't opening the folder but instead choosing it as what to add or you are not selecting 'all files' in that drop-down box.


As far as I know the script that cymbaline42 has linked to works and is benign (harmless) but I haven't tried it because I can write the .xml file myself.

---

