---
title: "stop the music already"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by moheganer2 on 2010-11-08
whenever i click on places-no matter which folder-audacious takes over and starts playing music files.i had the same problem with amarok which is why i got rid of it.i cant even access my home folder anymore, Anyone else run across this problem?

---

### Post by coffeecat on 2010-11-08
It's not actually the fault of Audacious or Amarok - there's nothing wrong with them - it's simply that the opening of folders has become associated with one of the media players. I had this once when opening a folder with DVD contents with VLC.

Go to the Places menu and click on 'Computer'. Does this open a Nautilus window? If so, navigate to your home folder. Now right-click on any folder within your home and click on 'Open with....' Select 'File Browser' from the list, make sure the 'remember this application' box is ticked and then click on 'Open'. This should reassociate folders with Nautilus.

---

### Post by moheganer2 on 2010-11-08
followed your instructions and it seems to have worked although it stills lists open with amarok first.is there any way to remove this from the open with menu?i couldnt find anything in properties.

---

### Post by coffeecat on 2010-11-08
> **moheganer2 said:**
> followed your instructions and it seems to have worked although it stills lists open with amarok first.is there any way to remove this from the open with menu?i couldnt find anything in properties.

Good point. I see that my system still shows 'open with VLC'. There must be a hidden configuration file in ~ which deals with this, and I vaguely remember reading a thread about it, but I can't remember the details. If I find something I'll post back.

---

### Post by nothingspecial on 2010-11-08
The files are at 

~/.local/share/applications

The files in question are defaults.list and the mimeapps.list

You need to edit them

---

### Post by moheganer2 on 2010-11-08
thanks for your help-i will mark this as solved.

---

