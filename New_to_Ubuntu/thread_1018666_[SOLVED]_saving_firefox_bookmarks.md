---
title: "[SOLVED] saving firefox bookmarks"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by som1special2 on 2008-12-22
Do you know how to save firefox bookmarks/settings to file? I am installing xubuntu and do not want to go through the process of doing everything manually. Thanks

---

### Post by taurus on 2008-12-22
Bookmarks -> Organize Bookmarks ->  Import and Backup -> Export HTML.

---

### Post by Toshibawarrior on 2008-12-22
If you want to backup everything in Firefox (add-ons, settings, bookmarks, etc) simply go to your /home folder and make hidden files visible (by using CTRL+H in GNOME) and then go to **.mozilla** folder, then  **firefox** and then inside you'll see a folder with 8 random charaters and a .default, it says something like **j1hg8eln.default** go into that folder and copy ALL of it's contents into a flash drive or any other media. 

And when you're in the new install Xubuntu (make sure you run firefox at least once for the correct folders to appear) go into **/home/.mozilla/firefox/xxxxxxxx.default**(the exact same folder you visited in the other isntall) and erase everything. Then copy all of the contents of the old profile folder (the ones you saved to an external media) and VOILA! When you start Firefox the next time everything will be exactly like you had it before!

I think I was clear enough but if you don't understand something just ask! ;) Hope this helps!

---

### Post by dgoosens on 2008-12-22
get the foxmarks addon for FF...
works great... and it even takes care of your passwords if you want it to...

---

