---
title: "Accidentally deleted menu items...need help!"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by Andy06 on 2009-06-28
So I uh...was using the main menu editor tool under System>preferences>Main Menu

And umm....on the left there is the option to untick boxes to hide them, but since there is a Revert to default button on the bottom, I instead selected lots of items from the right side and hit "Delete" instead and whoosh, they disappeared.

So obviously I hit the revert button and it dint.....revert, it just unhides the things that are currently there but does not bring back what was deleted.
So logically..........I deleted some more entries to test my theory and yeah......it doesn't bring them back.

What do I do now? I have only half a System>administration menu
And yea I just had to test it on the important administration section, I just could not test it in an innocuous menu like the Places or Apps one. My IQ reading for today is probably not in 3 figures.

Thanks

---

### Post by Amilo1718 on 2009-06-28
you might try ```
alacarte
``` using the CLI ;)

---

### Post by MasterProg on 2009-06-28
Try "Revert" button in Alacarte. If it doesn't work try this:

As far as I know, when you delete an item from menu, it is not actually deleted - they are just marked as hidden.

Go to *~/.local/share/applications*, edit every file with *.desktop* extension, find the line *Hidden=true* and replace *true* with *false*.

You can use this command to find out which items are hidden:
```
cd ~/.local/share/applications
grep -l "Hidden=true" *.desktop
```

There should definitely be a program that would do that automatically, can't think of one, though.

Hope that helps. ;)

---

### Post by Andy06 on 2009-06-28
Amilo1718,

alacarte is the same as the main menu editor I used to cause the whole mess in the first place hehe. It does not allow you to restore you pristine menu configuration. The revert button is a lying, misleading and nefarious sham :P

> As far as I know, when you delete an item from menu, it is not actually deleted - they are just marked as hidden.

Go to ~/.local/share/applications, edit every file with .desktop extension, find the line Hidden=true and replace true with false.

You can use this command to find out which items are hidden:

Masterprog,

Does this work for only one menu section/subsection or does it work for items deleted from the apps, places as well as system prefs and system admin menu?

I also have a new question. alacarte is the app named as menu editor in the system>preferences menu right? 
Then what is this thing called "menu editor" in the add/remove programs. Its not alacarte since alacarte is listed separately in Synaptic and this "menu editor" in add/remove is listed as gnome-menus in synaptic.

Thanks

---

### Post by ajgreeny on 2009-06-28
Try renaming your ~/.gconf/apps/panel folder to see if that gets rid of the configuration you have mistakenly set up.

---

### Post by MasterProg on 2009-06-28
It works for all deleted items, in System Preferences and Administration menus as well. I don't know if it works for Places menu - I have never tried to alter it in any way.

---

### Post by Andy06 on 2009-06-28
ajgreeny,

> Try renaming your ~/.gconf/apps/panel folder to see if that gets rid of the configuration you have mistakenly set up. 

That dint quite work. It reset the panel settings and everything about the panels but it did not restore the menus. Oh well, at least now I know what to do when I screw up the panel :P

But I think you had the right idea, if deleting/renaming the whole panels part restores panels to default. Is there a separate settings folder for Menus which I could rename, perhaps that would restore the menus configuration. Also about those packages I mentioned earlier, would removing and reinstalling the menu package help?

Thanks a lot.

P.S Just in case someone has these problem in the future and is referring to this thread, a real gem is the GNOME DO app, sure you can't see any of the deleted items in the menu, but you at least don't lose easy access to them as long as you have GNOME DO installed.

---

### Post by Andy06 on 2009-06-28
Ok the problem just got more absurd.
The alacarte (system>preferences>main menu) just stopped working.

I can execute it when I sudo it, otherwise it doesn't run when I click on it.

Typing alacarte into the terminal brings up this error message:
```

Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 50, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 59, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 63, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/Raptor/.config/menus/applications.menu'
```

Is this because I messed with the gconf/apps/panel folder and those .desktop files?

Thanks

---

### Post by james.brantley on 2009-06-28
> **Andy06 said:**
> So I uh...was using the main menu editor tool under System>preferences>Main Menu

And umm....on the left there is the option to untick boxes to hide them, but since there is a Revert to default button on the bottom, I instead selected lots of items from the right side and hit "Delete" instead and whoosh, they disappeared.

So obviously I hit the revert button and it dint.....revert, it just unhides the things that are currently there but does not bring back what was deleted.
So logically..........I deleted some more entries to test my theory and yeah......it doesn't bring them back.

What do I do now? I have only half a System>administration menu
And yea I just had to test it on the important administration section, I just could not test it in an innocuous menu like the Places or Apps one. My IQ reading for today is probably not in 3 figures.

Thanks

[SIZE=2]Hello, you might try right clicking on the panel then select[/SIZE] "add to panel" scroll down till you find "main menu" select it and then it will place itself on the panel after that right click on your partial menu then select "remove from panel" and you will be left with the full main menu that you placed there. Hop this helps!

---

### Post by Andy06 on 2009-06-28
No that does not work. The configuration of the new menu is exactly the same as that of the old menu. Even if I delete the old menu first and THEN add the new one, it comes back with the same config. Maybe if I can somehow delete the configuration folder like ajgreeny recommended for the panel (Now where would that be for the menus?)

---

### Post by drs305 on 2009-06-28
> **Andy06 said:**
> But I think you had the right idea, if deleting/renaming the whole panels part restores panels to default. Is there a separate settings folder for Menus which I could rename, perhaps that would restore the menus configuration. 

The user menus are controlled at least in part by two files in  ~/.config/menus: applications.menu and settings.menu  

These two files are also influenced by the same file names in /etc/xgd/menus  although I would not mess with these.

---

### Post by Andy06 on 2009-06-28
Ok understood. Won't play with those.

But unfortunately, my problem is still not solved. Moreover, the menu editor won't launch without privileges now. :(

---

### Post by swisstone198 on 2009-06-28
> **Andy06 said:**
> Ok understood. Won't play with those.

But unfortunately, my problem is still not solved. Moreover, the menu editor won't launch without privileges now. :(

What are the permissions on 
/home/vineet/.config/menus/applications.menu

---

### Post by MasterProg on 2009-06-28
Does this file exist? */home/vineet/.config/menus/applications.menu*

If so, try
```
sudo chown vineet:vineet /home/vineet/.config/menus/applications.menu
sudo chmod 644 /home/vineet/.config/menus/applications.menu
```

---

### Post by Andy06 on 2009-06-29
> What are the permissions on
/home/vineet/.config/menus/applications.menu 

The evil thieving root has taken over it. It also has a locked emblem on it.
What would have caused root to take it over and for permissions to change?

> Does this file exist? /home/vineet/.config/menus/applications.menu

Yes it does. I tried your commands and at first nothing happened. Then I saw settings.menu and that too was locked (root permissions needed), so I ran both your commands for that too and now I can run menu editor without privileges. Thanks

Now to fix the menu itself......

---

### Post by sasquatch74 on 2009-06-29
Hi,
Did you try deleting applications.menu and settings.menu in your /home/vineet/.config/menus folder?  
I just tried deleting these two files and it restored the default Applications, Preferences, and Administration menus.  
I made a backup of the existing files by renaming them applications_old.menu and settings_old.menu. Then I deleted the applications.menu and settings.menu that appeared after renaming.  
Then the default menus were resorted.

Does anyone see a problem with this?

Best of luck

Actually, the defaults were restored for me right after renaming the two files.  New applications.menu and settings.menu files appear when I open the Edit Menu tool.

---

### Post by Martje_001 on 2009-06-29
If you haven't got any trouble with resetting all you settings regarding the desktop, try:
```
sudo rm -r .config .gconf .gconfd .gnome2
```
sudo --> Super User Do (to get you root privileges)
rm --> remove
-r --> recursive (so it does delete underlying folders and files)
the rest --> names of directory's.

---

### Post by Andy06 on 2009-06-29
Ok so sasquatch74 nailed it I think. That's pretty automated and deleted the menu settings files.

Any other/better recommendations still welcome :)

---

### Post by Naren-Karma on 2009-09-19
Dear All,
Accidentally I deleted add/remove tool from main menu. Now I am unable to restore this   on application menu. Anybody  can help me to appear this icon again in same place.
regards
Naren

---

### Post by drs305 on 2009-09-19
> **Naren-Karma said:**
> Dear All,
Accidentally I deleted add/remove tool from main menu. Now I am unable to restore this   on application menu. Anybody  can help me to appear this icon again in same place.
regards
Naren

Naren-Karma,

First, welcome to Ubuntu.

If you click on the "Main Menu" icon on the top panel or on the menu bar ("Applications Places System" bar), you can select "Edit Menus". Then, at the bottom, click on "Revert" to restore the original menu items, which should include Add/Remove.

---

### Post by Naren-Karma on 2009-10-05
Dear sir,
I tried this but not get success yet.. I explored all admin settings related to menu and its sub-contains.

---

### Post by tom66 on 2009-10-05
Try opening a Terminal, and type "alacarte". What do you get?

---

### Post by drs305 on 2009-10-05
When you open "alacarte" as mentioned in the previous post, or open the main menu for editing via right click, Edit Menus (both should do the same thing):
Go toward the bottom and click on System, Administration.
In the right pane, do you see an unticked "Add/Remove Applications"?
If so, enable it, press Close, and you should be done.

If you don't see it in the right pane:
Press "New Item"'
Name: Add/Remove Applications
Command: /usr/bin/gnome-app-install
Comment: Install and remove applications
The icon should automatically appear.
Close.
Make sure "Add/Remove Applications" is enabled in the right pane.

---

### Post by Naren-Karma on 2009-10-06
Thanks, Now I can access Add/Remove link in my application menu. Thanks for support.
Regards - Naren

---

### Post by Sateros on 2010-12-07
> **Andy06 said:**
> So I uh...was using the main menu editor tool under System>preferences>Main Menu

And umm....on the left there is the option to untick boxes to hide them, but since there is a Revert to default button on the bottom, I instead selected lots of items from the right side and hit "Delete" instead and whoosh, they disappeared.

So obviously I hit the revert button and it dint.....revert, it just unhides the things that are currently there but does not bring back what was deleted.
So logically..........I deleted some more entries to test my theory and yeah......it doesn't bring them back.

What do I do now? I have only half a System>administration menu
And yea I just had to test it on the important administration section, I just could not test it in an innocuous menu like the Places or Apps one. My IQ reading for today is probably not in 3 figures.

Thanks

To regain inadvertently removed entries, go to ~/.local/share/applications and *_delete_     ***.desktop** files associated with the applications ( "rhythmbox.desktop" for Rhythmbox Music Player ). You can safely undo this by **Restore** at the Trash.

---

### Post by freddiejberg on 2011-02-19
Made quick attempt with posted tips, but do not think the solutions posted apply to my set up. Still pretty much a novice, so any help, tips (e.g., key commands - I do not use a mouse) are appreciated. Many thanks.

---

### Post by Sateros on 2011-02-19
> **freddiejberg said:**
> Made quick attempt with posted tips, but do not think the solutions posted apply to my set up. Still pretty much a novice, so any help, tips (e.g., key commands - I do not use a mouse) are appreciated. Many thanks.

If you accidentally deleted an item from Main Menu ( System > Preferences > Main Menu, at the top Panel), you should see <item-name>.desktop in **/home/<username>/.local/share/applications** ( as **.loca**l is a hidden folder you need to check Show Hidden Files under View on the Menu bar).

Let's take Mahjongg ( Applications > Games > Mahjongg ) as an example. I deleted that from Main Menu, then***  ma******hjongg.desktop*** showed up in the directory I mentioned above. I deleted that ( moved to Trash ) and the entry was re-created in Main Menu instantly.[LEFT]
[IMG]http://www.answers.com/main/images/close.gif[/IMG] 
[/LEFT]

---

### Post by lifeboy on 2011-07-03
> **Sateros said:**
> If you accidentally deleted an item from Main Menu ( System > Preferences > Main Menu, at the top Panel), you should see <item-name>.desktop in **/home/<username>/.local/share/applications** ( as **.loca**l is a hidden folder you need to check Show Hidden Files under View on the Menu bar).

Let's take Mahjongg ( Applications > Games > Mahjongg ) as an example. I deleted that from Main Menu, then***  ma******hjongg.desktop*** showed up in the directory I mentioned above. I deleted that ( moved to Trash ) and the entry was re-created in Main Menu instantly.[LEFT]
[IMG]http://www.answers.com/main/images/close.gif[/IMG] 
[/LEFT]

:cool:

I'd like to add that there is an additional entry or more in ~/.config/menus (where ~ is the standard replacement for the user's home directory).

I had the problem with the "NX Client for Linux" menu which also got deleted due to poor mousing from my side, and I found there merge files in this directory, which I had to remove to restore the menu in it's entirety.  

As was mentioned, the trash bin allows for easy restoration of a file if the wrong one was deleted in this process.
____________________________________________________

I blog at [http://lifeboysays.giesler.za.net](http://lifeboysays.giesler.za.net) and try to log my issues there for my own and others' benefit.

Ubuntu ***Lucid*** again after a ***dismal failure on Natty's part*** to run properly on both my desktop and laptop, partly caused by my GeForce FX 5500 being unsupported and my notebook also being *'only'* a Centrino with Intel graphics. Both do their work very well without Nutty Natty, thank you! :(

---

### Post by countryranger on 2012-01-02
Deleting files in ~/.local/share/applications worked for me in Lubuntu also...

---

