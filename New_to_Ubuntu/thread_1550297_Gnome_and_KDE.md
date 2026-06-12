---
title: "Gnome and KDE"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by crew51m on 2010-08-10
I remember in ubuntu 7.10, I could switch btween Gnome and KDE for a change in pace, can I still do it in 9.04? I know I had to log out, choose which I wanted to use. KDE wasnt too good on my old laptop but I would like to try it on my new one.

---

### Post by sandyd on 2010-08-10
> **crew51m said:**
> I remember in ubuntu 7.10, I could switch btween Gnome and KDE for a change in pace, can I still do it in 9.04? I know I had to log out, choose which I wanted to use. KDE wasnt too god on my old laptop but I would like to try it on my new one.
yup,the KDE login screen has an option for choosing gnome/kde

---

### Post by ubunterooster on 2010-08-10
Yes, Log out. When going to log back in there is a drop-down (actually pull-up here) menu titled "sessions" Choose the session KDE/ Gnome that you want

Edit: Carlee beat me.

---

### Post by crew51m on 2010-08-10
Thanks.

---

### Post by crew51m on 2010-08-10
I just went to change, only gnome and xscript was listed, also if I remember I had to load KDE.

---

### Post by ubunterooster on 2010-08-10
did you ```
sudo apt-get install kubuntu-desktop
```

---

### Post by crew51m on 2010-08-10
Not yet I will do tomorrow, I also found it in synaptics.

---

### Post by ubunterooster on 2010-08-10
Okay, keep us updated. :D

---

### Post by crew51m on 2010-08-11
Loaded it, looks cool, everything works, even 3d driver, except no Internet, there is not even an icon for the connection, I looked and I cant find the connection. I tried firefox and no connection.

---

### Post by crew51m on 2010-08-11
Found the icon. It looks like a plug. It is working good.

---

### Post by TriBlox6432 on 2010-08-11
The thing I don't like about it is that it installs all the KDE applications onto my Gnome.  I wish the KDE apps would stay in KDE and the gnome apps would stay in Gnome.

---

### Post by Vaphell on 2010-08-11
you can run them so why shouldn't they be listed?

---

### Post by TriBlox6432 on 2010-08-12
I just think it's a little ridiculous when I'm in standard Ubuntu to have two versions of terminal (one for KDE), KOffice in addition to Open Office, etc.

---

### Post by ubunterooster on 2010-08-12
use ```
alacarte
``` to edit the gnome menu.

---

### Post by chrisinspace on 2010-08-12
You can edit the menus so the launchers for the applications you don't want to see are not displayed.  In Gnome, right-click on the menu and choose edit.  Just un-check the items you don't want in your menu.

---

### Post by bcfieldi on 2010-08-12
I decided to install KDE too after seeing this thread, I like it, but there are some things that carried over to Gnome... the mouse cursor is now the way it looks in KDE, and when I restart it says Kubuntu now, even though I told it when I installed KDE that I wanted Gnome to be my primary desktop. It's not really a huge deal... they're just aesthetics but I'm not sure if they might be symptoms for other issues. Any thoughts?
 - Running lucid.

---

### Post by ubunterooster on 2010-08-12
The new DE taking over the splash screen is annoying but completely harmless, I would also like to find a way to fix it.

---

### Post by techunit on 2010-08-12
When ever I try this and switch back to gnome the dang mouse pointer is still stuck on the Oxygen theme, and I can't change it!

---

### Post by bcfieldi on 2010-08-12
> **techunit said:**
> When ever I try this and switch back to gnome the dang mouse pointer is still stuck on the Oxygen theme, and I can't change it!

I didn't like the oxygen cursor either. Figured it out. You have to change it while logged in KDE. To get to it go to Kickoff > 
Computer > System Settings > Keyboard and Mouse > Mouse > Cursor Theme and click the DMZ White theme to use the theme Gnome starts with originally. Hopefully that fix will stick when you log into Gnome again.

Update: Welp, it fixed it in KDE but when I log back into gnome, the standard cursor is still oxygen theme... I'm stumped.

---

### Post by crew51m on 2010-08-13
What rooster said, my splash now says Kubuntu, did the same thing on my last computer, is there a way to change back to the Ubuntu screen?

---

### Post by klytu on 2010-08-13
> **crew51m said:**
> What rooster said, my splash now says Kubuntu, did the same thing on my last computer, is there a way to change back to the Ubuntu screen?

I'm not sure but I think you can use the command update-alternatives to do this. Try: ```
update-alternatives --get-selections
``` Look for a selection on the left like usplash or plymouth and then try ```
sudo update-alternatives --config
``` with the selection you found earlier.

---

