---
title: "Deleting folders in the &quot;Places&quot; menu..."
date: 2009-08-16
forum: New to Ubuntu
---

### Post by BarefootSoul83 on 2009-08-16
I recently dragged a folder into the "Places" menu that I did not intend... How do I delete it?

---

### Post by Schendje on 2009-08-16
Open Nautilus, they'll be in the left window.

Right-click on the folder you want to delete -> Remove.

Hope that helps. :)

---

### Post by Rocket2DMn on 2009-08-16
You should be able to open nautilus and remove it from the left pane by right clicking.  If you don't see the pane on the left side, hit F9 or go to View->Side Pane.  File systems, network places, and the Trash are listed at the top, and the lower part shows your Bookmarks.

---

### Post by BarefootSoul83 on 2009-08-16
right click does not work in the Places folder...

and in Nautilus I cant see the folder I want to delete...much less the places folder

---

### Post by Schendje on 2009-08-16
No, right-click only works inside Nautilus.

Do you have the left sidepane in Nautilus? Like Rocket2DMn said, the Places folders are in the lower left, beneath the drives/network/trash.

---

### Post by techstop on 2009-08-16
Alternatively, open Nautilus (eg, Places>Home Folder), then Bookmarks>Edit Bookmarks. Add or remove whatever you like.

Anything that shows up in "Places" is a Bookmark.

---

### Post by BarefootSoul83 on 2009-08-16
Thats the funny thing...there are no bookmarks

---

### Post by corncob on 2009-08-16
> **BarefootSoul83 said:**
> right click does not work in the Places folder...

and in Nautilus I cant see the folder I want to delete...much less the places folder

Are you sure you haven't already deleted it?  Or are you sure you succeeded in dragging it into the Places menu to begin with?

---

### Post by BarefootSoul83 on 2009-08-16
yeah pretty sure... I go to "Places" and its all the normal stuff

Home
Desktop
Documents
Music 
Pictures 
Video
Cypress Hill - Los Grandes Exitos en Espanol. (<--the one I want to get rid of)

---

### Post by corncob on 2009-08-17
> **BarefootSoul83 said:**
> yeah pretty sure... I go to "Places" and its all the normal stuff

Home
Desktop
Documents
Music 
Pictures 
Video
Cypress Hill - Los Grandes Exitos en Espanol. (<--the one I want to get rid of)

When you get this drop down menu like you're showing us, select Cypress Hill....  When the window opens click on the EDIT menu then on  "Move to Trash".  I haven't tried this myself since I don't wanna remove any of my folders but it looks like the way to go.

---

### Post by tarps87 on 2009-08-17
[attach]125217[/attach]

---

### Post by BarefootSoul83 on 2009-08-17
nope...no dice... the "move to trash" button is grayed out...=-(

---

### Post by tarps87 on 2009-08-17
What move to trash? If you are trying to remove it from the places side bar then to is called remove, if you are trying to remove the file from the file system it sound like you do not have permission to remove it

---

### Post by BarefootSoul83 on 2009-08-17
I attached my screenshot... notice I'm in nautilus as "root" but theres nothing in the bookmarks part....

---

### Post by tarps87 on 2009-08-17
That's because the 'bookmark' is your not roots. You should only login as root or use sudo when it is necessary, as root you have the power to wipe everything of you machine.
Open nautilus as the user with the 'bookmark' (probably your user) right click -> remove.

---

### Post by BarefootSoul83 on 2009-08-17
lol...sorry this is such a pain... check it out though... its not in the nautilus either (and yet it remains in my "places" menu)

---

### Post by techstop on 2009-08-17
Try this.

Go to your Places menu, and open Home.

Press Ctrl + H to show hidden files.

Right-click on .gtk-bookmarks, Copy, then Paste to make a backup copy.

Right-click on .gtk-bookmarks again (the original version) and open it with a text editor.

Delete the offending line, and save.

Your Places (and Bookmarks) should be updated.

---

