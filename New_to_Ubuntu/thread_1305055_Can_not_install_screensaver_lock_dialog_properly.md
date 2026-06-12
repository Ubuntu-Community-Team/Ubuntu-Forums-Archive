---
title: "Can not install screensaver lock dialog properly"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by legolas_w on 2009-10-29
I tried to install a screen saver login dialog (lock dialog) in Karmic. I copied the content of archive which were some files with glade, gtkrc and png extension along with a directory containing some png files into the /usr/share/gnome-screensaver/ and changed the gconf entry as instructed.

I am talking about this theme:[http://www.gnome-look.org/content/show.php/New+Wave+Lock-Dialog+Theme?content=87773](http://www.gnome-look.org/content/show.php/New+Wave+Lock-Dialog+Theme?content=87773) but any other one I tried yelded the same result.

Now that the dialog is installed, Ubuntu is not using the dialog and still shows the defaul dialog.

I noticed that the provided file extensions are glade and gtkrc while the file already present in the directory are .ui files.

Does anyone here tried to install some lock dialog and got a positive result?

Thanks.

---

### Post by rahuldg on 2009-11-02
I am also experiencing the same issue.
I already had some lock dialog theme installed, but after upgrading to karmic, it turned to default one.
The config-editor settings are intact, but the theme doesn't change.
Even the "Leave Message" button also is missing from the dialog.
And the login screens also are now no more themable.
I don't understand, why would ubuntu will downgrade its features.

---

### Post by legolas_w on 2009-11-02
Hi,


I was unable to find a solution. If you did, please post a message here.

Thanks.

---

### Post by betrunkenaffe on 2009-11-03
There appears to have been some backend work done which has changed the implementation from a .glade to a .ui file format. On top of which, you can't just rename .glade to .ui (you can but it looks weird).

There's only one I found which supported Karmic specifically.

[http://opendesktop.org/content/show.php/Dark-Minimal+Lock+Dialog?content=109151](http://opendesktop.org/content/show.php/Dark-Minimal+Lock+Dialog?content=109151)

---

### Post by legolas_w on 2009-11-03
Thanks.

---

### Post by akamaleldin on 2009-11-03
> **legolas_w said:**
> I tried to install a screen saver login dialog (lock dialog) in Karmic. I copied the content of archive which were some files with glade, gtkrc and png extension along with a directory containing some png files into the /usr/share/gnome-screensaver/ and changed the gconf entry as instructed.

I am talking about this theme:[http://www.gnome-look.org/content/show.php/New+Wave+Lock-Dialog+Theme?content=87773](http://www.gnome-look.org/content/show.php/New+Wave+Lock-Dialog+Theme?content=87773) but any other one I tried yelded the same result.

Now that the dialog is installed, Ubuntu is not using the dialog and still shows the defaul dialog.

I noticed that the provided file extensions are glade and gtkrc while the file already present in the directory are .ui files.

Does anyone here tried to install some lock dialog and got a positive result?

Thanks.

An easy alternative to lock after login is to install xtrlock (from synaptic) then put it in your startup applications.

---

### Post by trainerjonathan on 2011-03-17
To install, copy both files in the archive to /usr/share/gnome-screensaver/ and change the /apps/gnome-screensaver/lock_dialog_theme gconf setting to the name of the theme.

For example:
[http://opendesktop.org/content/show.php/Dark-Minimal+Lock+Dialog?content=109151](http://opendesktop.org/content/show.php/Dark-Minimal+Lock+Dialog?content=109151)

---

