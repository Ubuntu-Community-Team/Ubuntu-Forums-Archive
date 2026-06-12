---
title: "firefox doesnt want to download anything"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by danschalow on 2009-07-12
firefox will not download anything, every time i try to download something it tells me that there is not enough space on the / drive, it doesnt even give me a letter. on my computer i have a :/u and a :/x how can i change firefox to download files into my :/u drive, i have tried clicking in edit>preferances going to downloads and then clicking browse for where to save the download, and nothing happens, no message or anything

it would be great if someone could help me out

Thanks
Dan

---

### Post by lisati on 2009-07-12
[LIST=1]
[*]Ubuntu doesn't use drive letters - see [here.]("https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows#Where%20To%20Put%20Your%20Files")
[*]Do you need to empty the trash?
[/LIST]

---

### Post by -=hazard=- on 2009-07-12
In default the download directory must be desktop, but anyway go from firefox to Edit -> Preferences -> Main and change the download location on your home folder.

---

### Post by ajgreeny on 2009-07-12
Is this a wubi install or a separate ubuntu partition on your drive?
Ubuntu will not show you any letters for drives as lisati says, but it must be possible to set the download destination for firefox, unless, of course your firefox is corrupt in some way.

Start by opening nautilus, the file manager, show hidden files and folders (Ctrl+H) and navigate to your home/username.mozilla folder and rename it by right clicking and calling it .mozillabak.  Now start firefox again.  It will make a new profile and it may work properly, though you will have to import your bookmarks from the old profile, but one step at a time.

---

