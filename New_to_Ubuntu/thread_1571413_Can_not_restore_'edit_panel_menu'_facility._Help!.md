---
title: "Can not restore 'edit panel menu' facility. Help!"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by candtalan on 2010-09-09
Help! I have a system (which was ubuntu 8.04.4, now just version upgraded to 10.04) in which the normal user2 has a non admin account and as admin user1, I originally locked the menus in the user2 desktop. I also edited the user2 panel menus to remove a lot of items.

I have now upgraded to 10.04, and although I have temporarily set the user2 now as an admin user, I cannot get the facility to edit the panel menus. I want to remove one or two items.

I have used gconf-editor in the past for this sort of thing I think, and this may the the key, but what do I exactly do please? 
tia

---

### Post by candtalan on 2010-09-09
mmm. I had already done the following

========================
Note: If you need to restore the panels to the original state, enter the following commands into the Terminal and re-start the system:
   1. sudo gconftool-2 --shutdown
   2. sudo rm -rf .gconf/apps/panel
   3. sudo pkill gnome-panel
========================

information was found at:
[http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm](http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm)


but it did not seem to work, but maybe I forgot to restart the system.
anyway, it now looks as if I can edit menus again.

---

### Post by beew on 2010-09-09
I don't think you need sudo. It is in your /home directory.

---

