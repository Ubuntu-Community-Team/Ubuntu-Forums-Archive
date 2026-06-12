---
title: "Places &gt; Bookmarks"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by Anybloodyid on 2009-06-28
Hi

Under the menu heading Places there is a bookmarks and in there are folders.
Hoe do I get the out of there and just have the folders show when I click places?

Thanks

---

### Post by VCoolio on 2009-06-28
If your number of bookmarks grows larger than a certain number (5 if I remember correctly) then they are automatically stored in a folder 'bookmarks'. No way around that.

---

### Post by nhasian on 2009-06-28
make sure you have 5 or less bookmarks and they will show up in Places.   if you have 6 or more they get put in the bookmarks subfolder.

---

### Post by mc4man on 2009-06-28
You can very easily build the repo gnome-panel source making 1 small edit and have as many entries as you wish (10 - 20 should suffice)

here's a post on it though there's a much easier, cleaner way to build (I think it's far better to build as a package, and in this case requires no prior building experience, 3-4 simple terminal commands and 1 edit

[http://ubuntuforums.org/showthread.php?t=1066964](http://ubuntuforums.org/showthread.php?t=1066964)

Just did on a jaunty live cd, works fine. (use hardy so wanted  to see if any differences in edit, build

The easiest edit is line 64 in gnome-panel-2.26.0/gnome-panel/panel-menu-items.c (change 5 to the number desired
```
#define BOOKMARKS_FILENAME      ".gtk-bookmarks"
#define DESKTOP_IS_HOME_DIR_DIR "/apps/nautilus/preferences"
#define DESKTOP_IS_HOME_DIR_KEY "/apps/nautilus/preferences/desktop_is_home_dir"
#define NAMES_DIR               "/apps/nautilus/desktop"
#define HOME_NAME_KEY           "/apps/nautilus/desktop/home_icon_name"
#define COMPUTER_NAME_KEY       "/apps/nautilus/desktop/computer_icon_name"
#define MAX_ITEMS_OR_SUBMENU   [COLOR="Blue"] 5 [/COLOR] 


```

To build as the same version package as is currently installed is quite simple and allows you to revert back to the original very easily if you don't like it. (if instr. are wanted will post

edit ; 
If you want to test, (though you can do the build for yourself in 15 -20 min. tops), this is the current **jaunty i386 **gnome-panel patched for 20 entries. It's done as same version # so will install as a 'reinstallion'..
While seen as the same version, the orig. repo package will still be considered an 'upgrade', to revert back simply let synaptic or update manger 'update' to the unpatched repo version.

[U]Don't let Gdebi try to install from this link, 'save file' to Desktop and d.click to install.
[/U]
After install log out and back in to 'activate'
When built as a package there are 6 packages produced, this is the only one needed if you don't up the version number.

If you up the version # (ex. 2.26.0-0ubuntu7-1) then a min. of 2 or 3 of the 6 need to be installed, the -devs kept in case needed, better to keep same ver. #, "reinstall' only the patched gnome-panel deb and lock in synaptic if desired to prevent an inadvertent 'upgrade

---

