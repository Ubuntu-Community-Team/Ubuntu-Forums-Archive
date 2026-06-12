---
title: "pidgin and indicator-applet"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by sacredsunder on 2009-04-24
Ok, so my problem is, in pidgin I want to know when I get a new message, but I don't care to know what they are saying. I would also like to be able to right click on the pidgin icon and be able to just quit. i haven't found a way to get either of those in the indicator-applet so is there a way to revert back to the old way pidgin ran in 8.10? Other than that Jaunt is excellent! 

Thanks!(sorry if this is posted like in a million places but I just couldn't find any reference for this)

---

### Post by mcduck on 2009-04-24
You can enable Pidgin's notification area icon in Pidgin's settings (Tools,/Preferences, on the Interface-tab set "Show system tray icon" to "Always"), and disable/configure the new notifications in Pidgin's plugin settings (Tools/Plugins/Libnotify popup).

---

### Post by sacredsunder on 2009-04-24
Oh man, thank you! I was really starting to think that might ruin the experience : p

---

### Post by PatricioLearner on 2009-08-23
Ubuntu is awesome...

---

### Post by Rasheeke on 2009-11-28
I would like to know why when switching form empathy to pidgin that indicator doesn't have pidgin with it.  It worked after the initial install but stopped showing up after the subsequent restart.

---

### Post by penkoad on 2010-01-20
I experienced the exact same behaviour.

I had pidgin indicated in the applet, so I de-installed empathy and after a restart no more indication...:-k

This is too bad.

Do you have any update on these issue ?

---

### Post by Dobbie03 on 2010-03-28
I am having the same issue as well.

---

### Post by obscenic on 2010-05-10
YES! FINALLY FOUND SOME MINIMAL CUSTOMIZATION!

I had to dig this up because evolution just totally disappeared from the applet one day....

Head on over to /usr/share/indicators/messages/applications

In there you'll find the applications that are listed under the messages icon. You can add and remove them.  Each entry is a text file. The format is just 1 line, and the file should be named the same as the application ie "evolution".
Format: 

```
/usr/share/applications/evolution.desktop
```

etc... You can head on over to /usr/share/applications to check out the name of the application you're trying to add if you're trying to add one that disappeared.

---

### Post by onclouds on 2010-07-15
nice thread..

but I'd like to have pidgin show up (like empathy) on the Chat entry... is this possible?

---

### Post by Karut on 2010-11-01
Is there any way that I cannot only disconnect or change my status via the gnome panel but also go online with Pidgin?

---

### Post by rio2000 on 2010-11-04
> **mcduck said:**
> You can enable Pidgin's notification area icon in Pidgin's settings (Tools,/Preferences, on the Interface-tab set "Show system tray icon" to "Always"), and disable/configure the new notifications in Pidgin's plugin settings (Tools/Plugins/Libnotify popup).

disable/configure the new notifications in Pidgin's plugin settings (Tools/Plugins/Libnotify popup) is Work for Me! Thanks.

*sorry for my bad english

---

### Post by checoimg on 2010-12-23
Pidgins notification area works excellent but I still want it to work with indicator applet.

---

### Post by inukaze on 2011-11-20
If you wanna make this :

[[IMG]http://img26.imageshack.us/img26/8246/lucidindicatorpidgin.png[/IMG]](http://imageshack.us/photo/my-images/26/lucidindicatorpidgin.png/)

Its simply :

1 - Purge "empathy" installation & install pidgin
2 - Open a terminal and use :

sudo rm -rf /usr/share/indicators/messages/applications/empathy
sudo rm -rf /usr/share/applications/empathy.desktop

# View if exist pidgin 

cat /usr/share/indicators/messages/applications/pidgin
[Desktop Entry]
Name=Pidgin
GenericName=Internet Messenger
Comment=Chat over IM.  Supports AIM, Google Talk, Jabber/XMPP, MSN, Yahoo and more
Exec=pidgin
Icon=pidgin
StartupNotify=true
Terminal=false
Type=Application
Categories=Network;InstantMessaging;
X-Ubuntu-Gettext-Domain=pidgin

ls /usr/share/applications/pidgin.desktop

and if exist "/usr/share/applications/pidgin.desktop" , edit it and change "Name=Pidgin" for "Name=Chat"

Save it.

sudo ldconfig && sudo update-menus
Ready i recommend , log off , and log in again
Now you can see , like me :-D

Wallpaper : [http://wallbase.cc/wallpaper/695487](http://wallbase.cc/wallpaper/695487)
Dock : Cairo-dock ( no OpenGL )
Compositor : Metacity or xcompmgr ( you can choise )
Globalmenu Applet

---

### Post by k3llz on 2012-04-01
So, I did everything that was posted above, and great, I can see the pidgin icon when I click on the mail envelope, but it doesn't light up and turn green the way it used to. And lib-notify isn't an option under the plug-in list, even when I down load the extention from the software center.

Any leads?

---

