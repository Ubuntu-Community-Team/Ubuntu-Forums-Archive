---
title: "Can't Remove User Home Folder From Desktop"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by Cfhs_1 on 2009-02-15
Ok, so here it is, I moved the user home folder to my desktop. The one that has the user name in front of it. Example: Jon's Home Anyway everything i try won't take it off. It doesn't show up in the desktop folder. Can anyone help me?

---

### Post by lavinog on 2009-02-15
Can you explain where the home folder came from? Did it come from windows?
Normally your Desktop is in your home folder so moving it would probibly do some weird things.

Otherwise it could be a permission issue. If you right click on the folder, and click properties, then permissions. You can change the folder permisions to create and delete files, then apply permissions to enclosed files

---

### Post by Cfhs_1 on 2009-02-16
> **lavinog said:**
> Can you explain where the home folder came from? Did it come from windows?
Normally your Desktop is in your home folder so moving it would probibly do some weird things.

Otherwise it could be a permission issue. If you right click on the folder, and click properties, then permissions. You can change the folder permisions to create and delete files, then apply permissions to enclosed files



The folder came from the places menu, I dragged it onto the desktop. when I go to permissions it says the permissions could not be determined...:(

---

### Post by bodhi.zazen on 2009-02-16
sudo unlink /home/your_user/Desktop/file_to_remove

If that fails ...

sudo rm -rf /home/your_user/Desktop/file_to_remove

---

### Post by lavinog on 2009-02-16
I just tried to drag and drop the home folder from the places menu to my desktop and got a "preparing to copy thousands of files" dialog.
dragging to the toolbar makes a link.
I canceled the copy operation before it started, but I might try it on a disposable computer later.

Something tells me that this should not be the normal behavior. Especially since there are posts that say it should make a shortcut.

---

### Post by Cfhs_1 on 2009-02-17
> **lavinog said:**
> I just tried to drag and drop the home folder from the places menu to my desktop and got a "preparing to copy thousands of files" dialog.
dragging to the toolbar makes a link.
I canceled the copy operation before it started, but I might try it on a disposable computer later.

Something tells me that this should not be the normal behavior. Especially since there are posts that say it should make a shortcut.



I can't remember when I first dragged it there... It was a while back. That's all I thought i was doing too, just making a shortcut, but apparently not....

---

### Post by Cfhs_1 on 2009-02-17
> **bodhi.zazen said:**
> sudo unlink /home/your_user/Desktop/file_to_remove

If that fails ...

sudo rm -rf /home/your_user/Desktop/file_to_remove





Neither work.... :(

---

### Post by InspiredIndividual on 2009-02-17
Does the folder show up in your Desktop directory? Specifically, what do you see for the Home Folder in the output of ```
ls -l /home/user/Desktop
```

EDIT: Another possibility: open the Gnome configuration editor (gconf-editor). Move to apps > nautilus > desktop and confirm that home_icon_visible is unchecked.

---

### Post by Cfhs_1 on 2009-02-17
> **InspiredIndividual said:**
> Does the folder show up in your Desktop directory? Specifically, what do you see for the Home Folder in the output of ```
ls -l /home/user/Desktop
```

EDIT: Another possibility: open the Gnome configuration editor (gconf-editor). Move to apps > nautilus > desktop and confirm that home_icon_visible is unchecked.




Thanks! that did it!!!! :D  your the best! lol

---

### Post by InspiredIndividual on 2009-02-18
You're welcome! It's nice to see I can help someone despite my very limited Ubuntu knowledge... :-D

---

