---
title: "Accidently deleted top panel-HELP"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by GiuHei3u on 2011-08-29
I accidently deleted my top panel in 11.04 and now cannot open any programs like Firefox, Mail , and Places, System, and Adminstration.
 
What can I do to reinstall the panel in the simplest way.
 
thanks

---

### Post by gandaran on 2011-08-29
> **gumshoegrant said:**
> I accidently deleted my top panel in 11.04 and now cannot open any programs like Firefox, Mail , and Places, System, and Adminstration.
 
What can I do to reinstall the panel in the simplest way.
 
thanks
there is a command to reset everything to default but I don't remember the command, you can also just right click the bottom panel and choose new panel then click again on the new panel and choose add to panel then find and add all the system menus and applets you need.

---

### Post by westie457 on 2011-08-29
> **gumshoegrant said:**
> I accidently deleted my top panel in 11.04 and now cannot open any programs like Firefox, Mail , and Places, System, and Adminstration.
 
What can I do to reinstall the panel in the simplest way.
 
thanks

Hi.
If you are using the classic Desktop Run this in a terminal```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by GiuHei3u on 2011-08-29
> **westie457 said:**
> Hi.
If you are using the classic Desktop Run this in a terminal```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```
 
Thanks Westie457!!!
I am back in business.
 
gumshoegrant

---

### Post by GiuHei3u on 2011-08-29
Have another problem related to the panel. I now have the panel and when I go to Places/Desktop all my icons and pics are there BUT when I go to upload some of the pics to my webbuilder the ubuntu window comes up that shows the items on my desktop instead of all the icons and pics showing there is only one pic. 
 
Anyone know how I can fix that?

---

### Post by westie457 on 2011-08-29
> **gumshoegrant said:**
> Have another problem related to the panel. I now have the panel and when I go to Places/Desktop all my icons and pics are there BUT when I go to upload some of the pics to my webbuilder the ubuntu window comes up that shows the items on my desktop instead of all the icons and pics showing there is only one pic. 
 
Anyone know how I can fix that?

What were you trying to do just before you deleted the top panel. The command to reset the panel restores to system default keeping everything that is known to the system and in the menus.
So if something is removed before the panel is deleted it stays deleted after the restore of the panel.

---

### Post by GiuHei3u on 2011-08-29
I was not doing anything other than looking at Places/Desktop and then accidently right clicking and deleting the panel! Strange way of deleting something.

But as I stated when going to Places/Desktop all my pics are there and also on the desktop itself but when using a program to upload some pics and the Ubuntu window opens and I click on Desktop to expose those pics for upload only one is showing. There seems to be a disconnect between the two.

Does this help?

thanks

---

### Post by westie457 on 2011-08-29
As clear as mud.
Never having used any form of web building software I do not know what to suggest to help. However I am prepared to learn about this and possibly learn something to suggest to help.

What is the name of the program you are using. This might take a bit of time for me to work out.

---

### Post by GiuHei3u on 2011-08-29
The fault is not with the Website Builder program but there is some glitch within the Linux Ubuntu program that is not show the 15 or so pics on this Ubuntu Desktop upload window but does show them on the Places/Desktop. 

Reinstalling the program, Ubuntu, would certainly wipe out everything on my system. Come to think of it when I want to email a picture from Shotwell or drag a pic to the desktop I have to start my Evolution email program and click on 'attachment' to attach that pic. I cannot right click the pic in shotwell or the desktop and hit send to because the email program doesnt see the pic. I state this because this particular problem developed about 3 weeks ago and seem now to have advanced into another area.

If this sounds confusing it is because of my poor communication skills. Perhaps I am better to end this thread.

thanks.

---

