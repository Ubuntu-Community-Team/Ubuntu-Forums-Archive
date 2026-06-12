---
title: "Mount Downloads folder on a different partition."
date: 2010-11-09
forum: New to Ubuntu
---

### Post by KaDMiO on 2010-11-09
Hi all:

I would like to know if there is a way to modify the path of the downloads folder. What I want to do is to access a separate partition I use for downloads, instead of having my own directory in the home folder.

This enables me to use the same space to download from multiple OSs.

Thank you very much.

---

### Post by AngusH on 2010-11-09
Assuming your using firefox, go to edit>preferences then click the general tab, change the save files to option and close the window. If your not using firefox post back with the browser you are using.
Angus

---

### Post by toekneewood on 2010-11-09
```

sudo mkdir /Downloads
sudo chown tony:tony /Downloads

```1. Change tony to your login name
2. If you are talking about firefox, then edit, preferences and change Downloads to /Downloads

hope this is what you are after.  You might want to change the "/Downloads" to something a bit more appropriate to keep your** / "root"**clean

---

### Post by KaDMiO on 2010-11-09
I am not talking about firefox, but the whole operating system.

For example, if I go to Places->Downloads, it should go to the partition I selected, instead of the regular /home/Downloads (although the path should be the same)

---

### Post by toekneewood on 2010-11-09
Now that is a good question.  I will have to do a bit of digging around

---

### Post by Verbeck on 2010-11-09
try editing your ~/.config/user-dirs.dirs file
****```
gedit ~/.config/user-dirs.dirs
```

---

### Post by davec64 on 2010-11-09
here you go!

The Downloads folder shown in Places is actually a bookmark (it also shows in nautilus).
By right clicking on the bookmark in Nautilus you can remove it.
Once you mounted your new location you want to save your downloads to you can navigate to the folder and drag it over to the Bookmarks area in Nautilus. Saying that you can drag any folder you want into this area to use as a shortcut. When you now look under Places it should show up.
I've got 2 additional HD's in my machine and have them set up for easy access using the Bookmarks.

Oh, and don't forget to change your apps so they save to the new location!

All the best  :)

---

### Post by toekneewood on 2010-11-09
Looks like this is the file you are looking for.  Please make sure you make a backup copy of your .config/user-dirs.dirs.
I have not tested this so, you might want to do it on a test machine or on a test account

```

cp ~/.config/user-dirs.dirs ~/.config/user-dirs.dirs.back
nano .config/user-dirs.dirs

```It looks something like this:
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"

---

### Post by KaDMiO on 2010-11-09
I'll try that. Thanks a lot!!

---

