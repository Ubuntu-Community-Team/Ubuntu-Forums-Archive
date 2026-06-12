---
title: "Change folder back to defaut icon"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by Dapilot1 on 2009-11-02
Hey I copied my files after a fresh install, how do I get my desktop/music/documents folder icons back to the ones that have the picture of what kinds of files are in them? That is the documents folder has the page on it and the download has an arrow on it. Or I guess, where are the default theme icons?

---

### Post by jrrader on 2009-11-02
In your home folder you'll find a hidden folder called .config (ctrl+h to view hidden folders).  Inside that folder you'll find a file called user-dirs.dirs.  Edit that to assign attributes to folders.  Mine looks like this:

```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```Put your copied folders into your home folder and then link them in that file.  After logging out and in again your folders *should* have those icons again.

---

### Post by ENigma885 on 2009-11-02
- Go to *System > Preferences > Appearance > Theme (tab)* and look for the previous theme u used to use before the upgrade.
OR
- If it wasn't a default icon theme and u installed it on ur own, u will probably find it in */home/$user/.themes* (this dot in .themes means the folder is hidden. So, u have to hit "ctrl+H" to show hidden items.) 
OR in */usr/share/themes*
- And the same goes with icons 
either in */usr/share/icons* OR */home/$user/.icons* 
- U can also use the customize button in the theme (tab) then icons to choose different icon set.

---

### Post by jrrader on 2009-11-02
Also, to give yourself ownership of everything in those folders (because they may belong to user 1003 or something after being copied and moved to a new install) use chown.  In terminal:

```
sudo chown -R username:usergroup /home/username
```

Replace username and usergroup with your user name.

---

### Post by TheAxeR on 2009-11-03
> **jrrader said:**
> In your home folder you'll find a hidden folder called .config (ctrl+h to view hidden folders).  Inside that folder you'll find a file called user-dirs.dirs.  Edit that to assign attributes to folders.  Mine looks like this:

```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```Put your copied folders into your home folder and then link them in that file.  After logging out and in again your folders *should* have those icons again.

Thank you so much.  I have been trying to figure this out for a while.  I love these forums.:)

---

### Post by Dapilot1 on 2009-11-03
How about for links that aren't always there. My music and videos are on my external and once its unplugged the user-dirs.dirs file unsets them. Is there a way to set the link icon to be the right ones always?

---

