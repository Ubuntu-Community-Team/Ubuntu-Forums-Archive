---
title: "Lost Contents of Application Menu"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by Tonanti216 on 2009-07-26
Stupid as I am ...... don't answer that! 

I have lost the contents of my Applications menu and cannot for the life of me figure out how to restore it.  I can see it and edit it as a "guest" but I cannot do either when I am signed in as "me" ...  How can I get back to the correct state .... I can't even find the "Terminal" to edit any files.

New and been tampering with the desktop look and feel was my mistake

---

### Post by cariboo on 2009-07-26
Right click on the top panel and select Add to Panel, then select Main Menu, or Cutom Menu. Main Menu just adds the Applications section, Custom Menu adds Applications, Places and System menus.

---

### Post by Tonanti216 on 2009-07-26
> **cariboo907 said:**
> Right click on the top panel and select Add to Panel, then select Main Menu, or Cutom Menu. Main Menu just adds the Applications section, Custom Menu adds Applications, Places and System menus.
Thanks, I will do that and only "report back" if I fail!  Thanks again

---

### Post by Tonanti216 on 2009-07-26
> **Tonanti216 said:**
> Thanks, I will do that and only "report back" if I fail!  Thanks again
OK, I did that but the "Applications" menu item does not contain any applications, in other words there is no drop down menu (there is a very thin white line under the word only) however, Places and Systems have the necessary drop downs.   The "Guest" desktop is entirely complete but I can't find a way to get back to where things were!

---

### Post by cariboo on 2009-07-26
When you right-click on Applications and select Edit Menus, does it show anything under Applications. See the screenshot. Make sure there are check marks in the menu items on the right, for the sections you want to show in the menu.

---

### Post by Tonanti216 on 2009-07-26
> **cariboo907 said:**
> When you right-click on Applications and select Edit Menus, does it show anything under Applications. See the screenshot. Make sure there are check marks in the menu items on the right, for the sections you want to show in the menu.
No, that is OK when I am signed in as a guest but not when signed in as me.  I originally tried to get that menu from Edit Menus and not being able to was what threw me! ... Novices ! .... I will learn though...

---

### Post by CatKiller on 2009-07-26
You could either, from the Edit Menus window, select Revert, to undo all the changes that you've made, or if that doesn't work do ```
mv ~/.config/menus ~/.config/menus.backup
``` to remove the existing menu configuration and get a new one created from the defaults. It's possible that you'll need to log out and log back in again for the new one to be created.

---

