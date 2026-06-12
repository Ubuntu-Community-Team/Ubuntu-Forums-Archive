---
title: "i need help installing themes..."
date: 2009-08-22
forum: New to Ubuntu
---

### Post by shadow mosis on 2009-08-22
I'm having a lot of trouble trying to installing themes, i honestly have no idea how to do it.  I would appreciate it if someone could help me in guiding me over the steps in accomplishing this...

---

### Post by Copernicus1234 on 2009-08-22
If its a tar.gz file, you can just open nautilus and drag and drop the file onto the Preferences-> Appearance window. Sometimes this doesnt work though because the files in the archive can be in subfolders etc.

You can unpack the tar.gz file and put it contents into /home/<username>/.themes as well. There is also .icons where you can put icons.

But yes, it can sometimes be a bit of a hassle the first few times. Then you'll learn and its easy.

So in the .themes folder, it should look like this for a Theme named Truth:

Folder: /home/<username>/.themes/Truth:

drwxr-xr-x 16 xxxxxxxx xxxxxxxx 4096 2009-04-18 14:35 gtk-2.0
-rw-r--r--  1 xxxxxxxx xxxxxxxx  200 2006-10-05 11:36 index.theme
-rw-r--r--  1 xxxxxxxx xxxxxxxx  204 2006-10-02 19:09 index.theme~
drwxr-xr-x  2 xxxxxxxx xxxxxxxx 4096 2009-04-18 14:35 metacity-1

(owner of files removed to protect the innocent)

**All folders starting with . are hidden by default in Nautilus so press CTRL+H to show them.**

---

### Post by shadow mosis on 2009-08-22
ohh god thank you so much, u i would always get stuck when they told me to put it in the themes folder and i couldnt find it this is really helpful... i will go give it a shot right now...thanks again...

---

### Post by Copernicus1234 on 2009-08-22
Good. Let me know how it worked out. :)

---

### Post by shadow mosis on 2009-08-22
now im actually stuck on how to install it... i put it on the themes folder and i not sure where to go from there...

---

### Post by Copernicus1234 on 2009-08-22
Go to System -> Preferences -> Appearance and see if you can find it. :)

---

### Post by shadow mosis on 2009-08-22
sorry from then on ima stuck...im not sure how to install it... thanks for helping me...

---

### Post by Copernicus1234 on 2009-08-22
If its in the .theme folder, its already installed.

Do a file listing of the contents of the .theme folder and the contents of your theme folder and post here please.

---

### Post by shadow mosis on 2009-08-22
darkerlceMurrina
gnome-theme--441159159.gtp...

i just realize i have the theme but it doesnt look like it should...

---

