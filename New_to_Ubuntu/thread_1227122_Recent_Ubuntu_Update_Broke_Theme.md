---
title: "Recent Ubuntu Update Broke Theme"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by bradm6 on 2009-07-30
The most recent update to Ubuntu (July29) broke my theme. I was using Human Theme with no problems, but after the update last night the computer rebooted in Clearlooks (blue) and will not let me change themes in the Appearance app. I'm using Metacity ("None" on the Visual Effects). Although the normal themes can be chosen in the Appearance app none of them take effect - the panel icons and window frames do not change to anything but the blue Clearlooks. I'd like to have my orange Human theme back. Was there something in the update that broke my themes, or is there a readjustment I have to make somewhere which got toggled by the new update?

---

### Post by tarps87 on 2009-07-30
Maybe not the neatest way but run the command **gconf-editor**
Now under
/ --> desktop --> gnome --> interface
set gtk_theme to Human and the same for icon_theme

As it sounds like the changes aren't being preformed on the fly you may need to reboot

Edit:

Some things to check:
```
cd ~/.gconf/desktop/gnome/interface
ls -l

```
you should see something like:
> 
-rw------- 1 tarps tarps 677 2009-07-30 16:27 %gconf.xml

note: tarps should be replaced with your username and the timestamp will be different
The things to check are the permissions (-rw-------)rw and owner (tarps)

---

### Post by bradm6 on 2009-07-30
Thanks for the reply .. I checked and both of those items have Human in them.

---

### Post by tarps87 on 2009-07-30
Ok, try
```
ls /usr/share/themes
```
The Human theme should be in there, if not that's the problem.

Can you change it to any other theme, like a custom one off gnome looks?

---

### Post by bradm6 on 2009-07-30
> **tarps87 said:**
> Maybe not the neatest way but run the command **gconf-editor**
Now under
/ --> desktop --> gnome --> interface
set gtk_theme to Human and the same for icon_theme

As it sounds like the changes aren't being preformed on the fly you may need to reboot

Edit:

Some things to check:
```
cd ~/.gconf/desktop/gnome/interface
ls -l

```you should see something like:

note: tarps should be replaced with your username and the timestamp will be different
The things to check are the permissions (-rw-------)rw and owner (tarps)

this was the result:

-rw------- 1 linux linux 663 2009-07-30 11:56 %gconf.xml

---

### Post by bradm6 on 2009-07-30
> **tarps87 said:**
> Ok, try
```
ls /usr/share/themes
```The Human theme should be in there, if not that's the problem.

Can you change it to any other theme, like a custom one off gnome looks?

Human is there .. I changed it to Crux in the gconf-editor = no effect
changed it back to Human = no effect
both of these after a restart

---

### Post by tarps87 on 2009-07-30
This is very strange.
Is linux your username?

Have you tried creating a new user and changing the settings then?

---

### Post by cgb on 2009-07-30
Having pretty much the same problem here as well since yesterdays updates.  Some parts of my theme/appearance settings are still in affect but I am unable to change any appearance settings at this point.  It allows me to make the changes but I do not see any change on screen.  Both of my computer users appear to be affected.

---

### Post by bradm6 on 2009-07-30
> **cgb said:**
> Having pretty much the same problem here as well since yesterdays updates.  Some parts of my theme/appearance settings are still in affect but I am unable to change any appearance settings at this point.  It allows me to make the changes but I do not see any change on screen.  Both of my computer users appear to be affected.

Perhaps someone will discover what it broke and correct it in an update. I've tried all the suggestions and nothing allows me to change the color in the window title bar nor the icons being used in the panels. I've tried reinstalling metacity, human theme, did a metacity --replace, tried all the themes showing up in the Appearance app, and tried all the suggestions above.

---

### Post by tarps87 on 2009-07-30
I can not think of anything that would be the problem, have have updated my system to the latest version and haven't experianced any issuses. I will carry on looking and post back if I can find anything

---

### Post by starcannon on 2009-07-30
After the updates gnome-settings-daemon would no longer fire up for me; I hosed out all the gnome and nautilus config files in my /home/myusername directory, resetting everything to default values, now I'll get my stuff all looking the way I like it again. Irritating, but sometimes stuff happens.

---

### Post by tarps87 on 2009-07-31
Out of interest is this with the 32bit or 64bit version? I have updated my 64bit machine, it will try with a 32bit install tonight. From what starcannon has posted I wouldn't expect it to make a difference.

---

### Post by cgb on 2009-07-31
Mine is actually the 64bit version.  A little bit of additional information I determined though is that it is only affected when remote login through nxserver.  Didn't realize the local connection was not affected until this morning since yesterday I was unable to login locally.  It does appear that it is a issue with the gnome-settings-daemon not being able to start when connected through nxserver in my situation.  Not sure why this has changed since the updates but it has.  In case anyone wants to take a look further, attached is my debug log when attempting to start gnome-settings-daemon.

---

### Post by rdoolen on 2009-07-31
I have to exact same issue. 

I just wanted to add that I tried going back to the old kernal and that didn't solve anything.

---

### Post by rdoolen on 2009-08-01
The problem is that gnome-settings-daemon is failing. To get it to start, you need to launch gconf-editor, go to apps/gnome-settings-daemon/plugins/keyboard and disable it. then gnome-settings-daemon can start.

This is a known bug. I found it seaching google, sorry I didn't write down where I found it.

---

### Post by cgb on 2009-08-01
> **rdoolen said:**
> The problem is that gnome-settings-daemon is failing. To get it to start, you need to launch gconf-editor, go to apps/gnome-settings-daemon/plugins/keyboard and disable it. then gnome-settings-daemon can start.

This is a known bug. I found it seaching google, sorry I didn't write down where I found it.

sweet, thanks this worked perfectly...

---

### Post by tarps87 on 2009-08-03
Glad you found the solution. After looking for nxserver and gnome-settings-daemon bugs I have found what appears to be the bug report:

[https://bugs.launchpad.net/freenx-server/+bug/399758](https://bugs.launchpad.net/freenx-server/+bug/399758)

---

