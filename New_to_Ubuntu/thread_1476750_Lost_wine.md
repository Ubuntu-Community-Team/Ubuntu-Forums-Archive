---
title: "Lost wine"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by redbook4574 on 2010-05-08
Hi 

I have lost wine from my applications menu, any idea how I restore it ???

---

### Post by jvc26 on 2010-05-08
Right click on the ubuntu menu on the panel, select edit menus, and that will open the alacarte application which edits the menus. You can then reenable it from there. (assuming you didnt accidentally remove the package)

J

---

### Post by ankspo71 on 2010-05-08
This should help if you uninstalled wine, and then installed it again later. I'm not sure why it does this, but uinstalling wine and then installing it again later could prevent the menu entries from reappearing. If this is the case, then try the following:

Open the terminal and type:
```
gedit ~/.config/menus/applications.menu
```

Then look for any <Deleted> and </Deleted> tags, to see if they are surrounding your wine menu entries. Remove those tags to unblock them.

Then click save. If it doesn't appear right away in your menu you will have to log out and log back in.
Hope it helps.

---

