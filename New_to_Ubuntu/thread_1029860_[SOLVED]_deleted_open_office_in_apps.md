---
title: "[SOLVED] deleted open office in apps"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by lad3391 on 2009-01-03
i was trying to fix another problem in my menu (which i got resolved) and i tried to delete a folder called other, and i accidently got rid of office. whats a quick way to get that back? all that was in it was the open office stuff that comes standard

---

### Post by drs305 on 2009-01-03
> **lad3391 said:**
> i was trying to fix another problem in my menu (which i got resolved) and i tried to delete a folder called other, and i accidently got rid of office. whats a quick way to get that back? all that was in it was the open office stuff that comes standard

Depending on how you deleted it, the entire contents may still be in your trash bin. In Hardy and later, your trash is in ~/.local/share/Trash/files

If you deleted it as root, check /root/.local/share/Trash/files

If you deleted it completely without it going into trash, reinstall it as you did before or install it via synaptic.

---

### Post by drs305 on 2009-01-03
> **lad3391 said:**
> i was trying to fix another problem in my menu (which i got resolved) and i tried to delete a folder called other, and i accidently got rid of office. whats a quick way to get that back? all that was in it was the open office stuff that comes standard

Depending on how you deleted it, the entire contents may still be in your trash bin. In Hardy and later, your trash is in ~/.local/share/Trash/files

If you deleted it as root, check /root/.local/share/Trash/files
Open nautilus as root with:
```

gksudo nautilus /root/.local/share/Trash/Files

```

If you deleted it completely without it going into trash, reinstall it as you did before or install it via synaptic.

---

### Post by mkvnmtr on 2009-01-03
Just a thought. Did you delete the program or just the icon? If you were messing with the menu maybe it is just the icon.

---

### Post by lad3391 on 2009-01-04
oh sorry for my lack of provided info. all i did was delete the menu icon. i was just wondering what route i would take to restore a) the office folder and icon picture b) the contents of this menu folder to how it was (i hadnt made any changes since installed ubuntu)

last time i did this it was with the wine menu. and i followed these instructions

sudo apt-get --purge remove wine
sudo rm -r /home/username/.config/menus

then i had to log out and log in

what if i just delete the menu config then log out and log in? would that rebuild my menu

---

### Post by jimmy the saint on 2009-01-04
right click the applications menu and click on "edit menus"
make sure the checkbox next to "Office" is checked.

---

### Post by lad3391 on 2009-01-04
thats where i accidentally deleted it from ;)

---

### Post by RomeReactor on 2009-01-04
Hi. I think reinstalling Open Office should restore the icons, but if you want to do it manually you can add them like this to the Office section:

* OpenOffice Database:
--Type: Application
--Name: OpenOffice.org Database
--Command: ooffice -base %U
--Comment: Manage databases, create queries and reports to track and manage your information.

Icon location: /usr/share/icons/Human/48x48/apps/ooo-base.png
---------------------------------

* OpenOffice Presentation:
--Type: Application
--Name: OpenOffice.org Presentation
--Command: ooffice -impress %U
--Comment: Create and edit presentations for slideshows, meeting and Web pages.

Icon location: /usr/share/icons/Human/48x48/apps/ooo-impress.png
---------------------------------

* OpenOffice Spreadsheet:
--Type: Application
--Name: OpenOffice.org Spreadsheet
--Command: ooffice -calc %U
--Comment: Perform calculation, analyze information and manage lists in spreadsheets.

Icon location: /usr/share/icons/Human/48x48/apps/ooo-calc.png
---------------------------------

* OpenOffice Word Processor:
--Type: Application
--Name: OpenOffice.org Word Processor
--Command: ooffice -writer %U
--Comment: Create and edit text and graphics in letters, reports, documents and Web pages.

Icon location: /usr/share/icons/Human/48x48/apps/ooo-writer.png

---

