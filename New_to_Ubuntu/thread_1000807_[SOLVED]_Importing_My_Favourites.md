---
title: "[SOLVED] Importing My Favourites"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by AdmBeatty on 2008-12-03
Is there any way to import My Favourites (IE6) into Firefox (convert to Bookmarks) if you haven't exported them to a HTML file?  Having just upgraded from Windoze to Ubuntu, I have my old 'favourites' folder full of .url files that Firefox won't recognise.  I have far too many to go to each one individually!

---

### Post by philinux on 2008-12-03
Can you not fire up windows and do this.
[http://kb.mozillazine.org/Firefox_:_FAQs_:_Import_IE_Bookmarks#To_export_your_IE_Favorites_to_a_file](http://kb.mozillazine.org/Firefox_:_FAQs_:_Import_IE_Bookmarks#To_export_your_IE_Favorites_to_a_file)

---

### Post by Michael.Godawski on 2008-12-03
I have also googled a bit and found only solutions which start with a html file...
Do you have access to a windows machine?
 > I have far too many to go to each one individually! 	
How many?

---

### Post by AdmBeatty on 2008-12-03
Unfortunately, I took the plunge and no longer have a windows computer...:redface:

---

### Post by philinux on 2008-12-03
Ok here's a work around for you.

Install wine from add/remove or synaptic

then install ies4linux
[http://www.tatanka.com.br/](http://www.tatanka.com.br/)

Once installed copy your uri files to ie's favorites folder
This is located here.
/home/username/.ies4linux/ie6/drive_c/windows/profiles/username/Favorites

Fire up ies4linux
Then export all your bookmarks then pick them up with firefox. ):P

---

### Post by Keen101 on 2008-12-03
> **philinux said:**
> Ok here's a work around for you.

Install wine from add/remove or synaptic

then install ies4linux
[http://www.tatanka.com.br/](http://www.tatanka.com.br/)

Once installed copy your uri files to ie's favorites folder
This is located here.
/home/username/.ies4linux/ie6/drive_c/windows/profiles/username/Favorites

Fire up ies4linux
Then export all your bookmarks then pick them up with firefox. ):P


yeah, i'd try that too.

sudo apt-get install wine

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by AdmBeatty on 2008-12-03
Installed Wine and IES4Linux following the instructions, but it only opens an 'Explorer Pane' with no toolbar or menus etc; essentially a blank terminal, although the right-click menu is that of IE.

---

### Post by philinux on 2008-12-03
> **AdmBeatty said:**
> Installed Wine and IES4Linux following the instructions, but it only opens an 'Explorer Pane' with no toolbar or menus etc; essentially a blank terminal, although the right-click menu is that of IE.

Thats weird mine looks like this. Even a nice icon on desktop.

From the menu apps>wine click configure wine choose say xp.
I think that might sort it.

---

### Post by AdmBeatty on 2008-12-03
Still no joy, although I suspect it may be the way IES4 is interacting with Wine; although I can find iexplore.exe in the 'C drive', it isn't coming up as a desktop icon, or an option in the wine menu (including uninstall programmes, which suggests it isn't instyalled in the first place!). 

Many thanks for all this! ; - )

---

### Post by philinux on 2008-12-03
Reinstall ies4linux and this time ask it to create a desktop icon.

Follow the instruction to the letter.

---

### Post by AdmBeatty on 2008-12-03
Wow! Up and running - 4th time lucky.  Could have sworn I didn't do anything different!  Many thanks for the help!

Regards;)

---

