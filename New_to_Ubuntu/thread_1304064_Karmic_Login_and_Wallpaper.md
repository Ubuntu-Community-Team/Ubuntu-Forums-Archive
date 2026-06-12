---
title: "Karmic Login and Wallpaper"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2009-10-28
Hey everyone I just upgraded to 9.10 and I've got what should be simple questions.

First, I don't want to be able to pick a user name, I want to be forced to type it.

Second, I'm trying to find the old Jaunty wallpapers because I'm not a fan of the Karmic wallpaper. I love one of the new themes, but the wallpaper has to go.


Any Karmic veterans out there?

---

### Post by ninjapirate89 on 2009-10-28
[http://beginlinux.wordpress.com/2009/03/27/ubuntu-904-wallpaper-no-jackalope/](http://beginlinux.wordpress.com/2009/03/27/ubuntu-904-wallpaper-no-jackalope/)

That has the two Jaunty wallpapers.

Edit -> Sorry I can't help with the login question. I haven't tried Karmic yet.

---

### Post by Lazy-buntu on 2009-10-28
Thanks for the reply. Karmic is pretty nice, the shut down speed was lightning quick on the first attempt, I'll have to try a second time. I mean it was off in about 4 seconds. Boot up time seems longer though for some reason. Maybe it's because there's two splashes before login then another splash screen.

It's brand new so I'll give it some time. The software center is pretty fantastic. My main gripe is having my user name displayed at login. I'm trying to find out how to fix that still.

---

### Post by Lazy-buntu on 2009-10-28
Oh and another thing: certain icons are missing from my menus. Like under Places, my connect to a server icon is missing and so is the search for files. Then, under System all the icons on the parent directories aren't showing (preferences, about gnome, etc.).

Edit: Ugh no sound either.

---

### Post by lavinog on 2009-10-28
[s]I noticed a setting in gconf-editor that looks like it can be used to disable the user list.  I will update after a restart.[/s]
Nevermind, it didn't work.

---

### Post by ranch hand on 2009-10-28
If you go to System>Preferences>Appearance and go the Interface tab you will find a box to lick on to show icons in your menus.  It is unchecked by default in 9.10.

This saves me the trouble of unchecking it but means that those that like the silly buggers must check it.  I have no idea why tis was changed.

Have you looked in the /usr/share/backgrounds directory?  This is where the wallpapers are for 9.10.
Some are pretty nice.

Your xsplash images live at /usr/share/images/xsplash.  These can be replaced by images the same size and resolution.  The GDM image comes from there too, it is bg_2560x1600.jpg.

As for the login.  There is a thread in the testing forum on that and I believe you can do what you want.  You will have to search there though.

  [http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)

That forum ends tomorrow and goes to the archieves.   I would check it out and bookmark it now.  There is a lot of great info there.  We have been busy.

---

### Post by lrcaballero on 2009-10-28
Try this:

System
administrator
user/groups
select your name/properties/ and make sure [COLOR=Navy]set password[/COLOR] is checked!!

Luis

---

### Post by Lazy-buntu on 2009-10-29
Thanks, I've got the icons back.

Now it's a matter of fixing my sound. It's strange because I've never had a problem upgrading before.

If I do lspci I see a sound device in there, but I've got no sound in any application or even at login.

---

