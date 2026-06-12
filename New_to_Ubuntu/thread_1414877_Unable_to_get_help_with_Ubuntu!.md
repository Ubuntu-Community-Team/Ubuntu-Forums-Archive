---
title: "Unable to get help with Ubuntu!"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by boxcorner on 2010-02-24
Hello
I am running Ubuntu 9.10 with GNOME version 2.28.1 & Firefox Namoroka version 3.6.2pre
When I click on the *Help - Get help with Ubuntu* icon in the bar at the top
a window opens, then after a while an error message is displayed:
"Unable to load page; The requested URI "file:///fakefile#index" is invalid"
The same thing happens when I click on *System* > *Help and Support*
When I click on  *System* > [I]About Ubuntu
[/I]a similar window with the *Help* icon in the top left-hand corner opens, but nothing happens.
When I click on* System > About GNOME* the window opens normally.
Could someone please tell me how to fix this?
Thanks in anticipation.
BTW - I think Ubuntu is great, the people here are very friendly & no, so I don't miss XP :D

---

### Post by ajgreeny on 2010-02-24
Try using synaptic to completely remove and then reinstall **ubuntu-docs**.  That might help.

You may need to do the same with **gnome-doc-utils**, but take care as that will remove five other dependencies. as well, which you will need to also reinstall afterwards.

---

### Post by davidryderuk on 2010-02-24
Hi,
A quick Google search brings up the following two posts.

[https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/396516](https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/396516)

[http://ubuntuforums.org/showthread.php?t=1323576](http://ubuntuforums.org/showthread.php?t=1323576)

Uninstalling "XULrunner 1.9.2" seems to be the easiest solution. You can quite easily find and uninstall this package using synaptic package manager. Since this package is associated with Firefox 3.6 (it was installed at the same time), you might loose firefox at the same time. 

There does seem to be a suggestion that completely reinstalling and updating Firefox 3.6 (and it's dependancies) could get both programmes to work simultaneously.

---

### Post by boxcorner on 2010-02-24
@ ajgreeny
Many thanks for your help.  I tried what you suggested.
Completely removing and reinstalling **ubuntu-docs **made no difference.
Likewise **gnome-doc-utils **& reinstalling the five dependencies.
However, now About Ununtu has gone AWOL.
Help icon remained in the top bar after **gnome-doc-utils** was completely removed.  
Have now removed it, as it seemed superfluous.

@ davidryderuk

 Have just checked the menu and strangely the *About Ubuntu* option has re-appeared, of its own accord, presumably because my machine has been re-booted during the intervening period.  So no further action is necessary, thanks. Nevertheless, thank you for your post.  I no longer recall what the menu originally contained, but it's currently: Prefs|Admin|Help & Support|About GNOME|About Ubuntu.  

One of things I've noticed about Ubuntu is that updates and other program changes seem to require fewer re-boots, than XP.

@ davidryderuk
Many thanks.  Uninstalling XULrunner 1.9.3 did the trick. Firefox (Namoroka) seems unphased by the change.   Is there an easy way to get the *About Ubuntu* option back?

---

### Post by davidryderuk on 2010-02-24
I just tried reinstalling the same program on my computer. The following brought the menu option back (I have no idea why):

1. Right click on the menu and select "Remove From Panel".

2. Right click on the empty space in the top left of the panel and select "Add to Panel".

3. Select "Menu bar" and then click on "Add".

4. Right click on the Menu bar applet and select "Lock to panel"

---

