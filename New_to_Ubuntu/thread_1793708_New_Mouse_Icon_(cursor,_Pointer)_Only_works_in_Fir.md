---
title: "New Mouse Icon (cursor, Pointer) Only works in Firefox"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by slayner117 on 2011-06-29
Basically I can install a new mouse theme (this is the one I have installed) [http://gnome-look.org/content/show.php/Pulse+Glass?content=124442](http://gnome-look.org/content/show.php/Pulse+Glass?content=124442)

It *will* work, however limited to only working in firefox. Outside of firefox 

EX: desktop, folders, anything. It will revert back to the default icon. I don't figure this is a firefox issue, because, well. It's not really an issue, it's the only one doing the --right-- thing. 


Anyway please help me with this issue I am running V. 11.04  thank you in advance.

---

### Post by jtarin on 2011-06-29
I helped you get this installed not long ago....but at the time you made no mention of using 11.04. [Here are instructions]("http://www.ubunturoot.com/2010/05/how-to-change-mouse-cursor-in-ubuntu.html") for getting it to work in 11.04.

> Alternatively, and without root permissions, you can do this in the home folder per user:

1. Open 'Appearance'

2. Click Install and choose the cursor tar package you downloaded. It should give you a 'Theme Installed Successfully.' Click 'Apply New Theme Now' and exit 'Appearance.'

3. Open your home folder and create a folder called 'default' in the folder /home/YOUR_USERID/.icons/

4. Go into the folder you just created and right click and create an empty file here. Open the file with gedit and past the line from the tip above '[Icon Theme] | Inherits=YOUR_ICON_THEME_FOLDER_NAME'

5. Save the file as 'index.theme'

6. Logout and log in. Presto! 

Compiz running is the problem.

---

### Post by slayner117 on 2011-06-29
Ah, Well I apologise for that. Thanks for the continued help!

---

### Post by jtarin on 2011-06-29
See my edit above your post.

---

### Post by slayner117 on 2011-06-29
I did, I'll mark this as solved now, I just did it and it works. Again thank you for your help both times now. Worked perfectly

---

