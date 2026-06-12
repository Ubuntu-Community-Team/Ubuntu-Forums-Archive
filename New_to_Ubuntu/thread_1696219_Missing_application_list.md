---
title: "Missing application list"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by hunternsf on 2011-02-27
While attempting to add new applications to my system, I have somehow hidden the list of applications that used to appear when I would click the Applications menu on the upper panel.  I still get the normal drop-down lists when I click Places and System, but nothing when I click Applications.  As I put my pointer over the word it says "Browse and run installed applications", but when I click, nothing appears.  I seem to have all of the applications, but the list itself is not accessible.  Does anyone know how to fix this?

---

### Post by emoguitarist06 on 2011-02-27
Try going to System > Preferences > Main Menu
and under Applications make sure what you want to show in your list (which of course are separated by sub lists like Accessories, Games, etc..) are checked

Let's see if that works ;)

---

### Post by vivek.pandey on 2011-02-27
> **hunternsf said:**
> While attempting to add new applications to my system, I have somehow hidden the list of applications that used to appear when I would click the Applications menu on the upper panel.  I still get the normal drop-down lists when I click Places and System, but nothing when I click Applications.  As I put my pointer over the word it says "Browse and run installed applications", but when I click, nothing appears.  I seem to have all of the applications, but the list itself is not accessible.  Does anyone know how to fix this?

remove the applet from the panel and then right click on panel->add to panel->menu bar see if this helps

---

### Post by hunternsf on 2011-02-27
Thanks for the response--When I go to System>Preferences>Main Menu, nothing happens. I don't get a window or anything that lists applications with check boxes.

Also, when I tried to right click on panel>add to panel>menu bar, it put an exact duplicate of the original three categories but with the same bug as before.  Places and System have populated drop-down lists, but still nothing for Applications.  I wish that I could perform some type of 'Restore Default Settings' command for the Main Menu.

---

### Post by vivek.pandey on 2011-02-27
k right click on the applications option in the panel. you will see the list of applications. try adding applications from there . see if  this works

---

### Post by SwatKat on 2011-02-27
If you want to restore just the menus, right click on applications or places or system in the menu bar -> edit menus -> revert. 
If that doesn't work I believe you can restore the panel to its default settings by following  the instructions in this thread
[http://ubuntuforums.org/showthread.php?t=1475584](http://ubuntuforums.org/showthread.php?t=1475584)
Then you might get the option of editing your menus and can add the required applications to the list

---

### Post by hunternsf on 2011-02-27
> **neo_aryan said:**
> k right click on the applications option in the panel. you will see the list of applications. try adding applications from there . see if  this works

When I right click on applications, I don't see a list of applications. With right click, I get 'Help', 'Edit Menus', 'Remove from Panel', 'Move', 'Lock to Panel'.  When I click Edit Menus, nothing happens. The only way that I can add applications is through Synaptic Package Manager.  However, even after I add the app to my system (and get the confirmation of it being downloaded and installed), it still doesn't appear under the Applications menu.  It seems like there is a 'Hide' command being executed somewhere, but I can't figure out where.  So, basically, I can't launch any applications directly.  For example, I have the full Open Office suite already installed, but I can't just launch the app and start a new document.  Is there a way to access and launch installed programs from 'File System' in the Places menu, kinda like opening the Programs folder in MS?

---

### Post by vivek.pandey on 2011-02-27
cant you see your applications in system->preferences->main menu?

---

### Post by hunternsf on 2011-02-27
> **neo_aryan said:**
> cant you see your applications in system->preferences->main menu?

Nope.  Nothing comes up, or opens, or appears when I go to system->preferences->main menu --the same as when I just click on Applications on the menu bar. I can't find a list of my installed programs anywhere.

Is there another forum or community or other troubleshooting site where you would suggest that I post this thread in order to get help with this problem?  It's incredibly frustrating.  I couldn't even open an Excel spreadsheet that someone sent me via email because I couldn't select OpenOffice as the application to open it after the virus scan had been performed. I really appreciate the time and attention that you've given my problem thus far.

---

### Post by vivek.pandey on 2011-02-27
check this out
[http://hatherly.com/blog/?p=17](http://hatherly.com/blog/?p=17)

---

### Post by hunternsf on 2011-03-02
> **neo_aryan said:**
> check this out
[http://hatherly.com/blog/?p=17](http://hatherly.com/blog/?p=17)

I couldn't find any directory named: ~/.config/. But searching within Filesystem for anything named applications.menu, I found these files:

/etc/xdg/menus/applications.menu

/usr/share/app-install/desktop/applications.menu

/etc/xdg/menus/kde4-applications.menu

 /usr/share/desktop-directories/X-GNOME-Menu-Applications.directory

They're all locked (read-only).  Which one should I delete?  My intuition isays either the 2nd or the 4th or both, but I didn't want to guess and possibly make things even worse.

:confused:

---

### Post by Brandel Valico on 2011-03-02
Fair warning this is how it was fixed in 2007. Not positive it will still work. But check out this thread [Fix missing Applications Menu]("http://ubuntuforums.org/showthread.php?t=554585&page=3")

---

### Post by hunternsf on 2011-03-11
> **Brandel Valico said:**
> Fair warning this is how it was fixed in 2007. Not positive it will still work. But check out this thread [Fix missing Applications Menu]("http://ubuntuforums.org/showthread.php?t=554585&page=3")
In the thread that came up from your hotlink, it stated:

"Just had this happen to me. My Applications menu stopped working. To fix  it I went Copied the information from the Applications menu found at   /etc/xdg/applications.menu
 
 To the one found in the Home Folder/.config/Menus/applications.menu"
 
I was able to find  the information from the Applications menu found at   /etc/xdg/applications.menu, but I was **not** able to find config/Menus/applications.menu in my Home folder.

My Home folder only contains 1 item, my personal folder, hunternsf.  How  can this be?  What am I doing wrong?  What should I be seeing when I  open the Home Folder?  

I tried to fix the problem of the missing Applications menu, by  upgrading from Lucid Lynx to Maverick Meerkat.  The applications menu  was still missing even with the upgrade to the newer release.  Should I  uninstall and then reinstall Ubuntu?

---

### Post by Brandel Valico on 2011-03-13
The .config folder is hidden by default in ubuntu. You need to press "Ctrl+H" while in the home (hunternsf) folder to show the hidden files. Then try copying over the information found in the file. By opening it up and copy pasting the text within to the one in config.

If you actually don't have the menu file. You will need to create it and name it and copy paste the script found a bit farther down in the link. 

Let us know if this solves the issue.

---

### Post by hunternsf on 2011-03-13
> **Brandel Valico said:**
> The .config folder is hidden by default in ubuntu. You need to press "Ctrl+H" while in the home (hunternsf) folder to show the hidden files. Then try copying over the information found in the file. By opening it up and copy pasting the text within to the one in config.

If you actually don't have the menu file. You will need to create it and name it and copy paste the script found a bit farther down in the link. 

Let us know if this solves the issue.
The fix worked perfectly!!!  Thanks a lot for your help Brandel!  Also, thanks to everyone else who posted  suggestions, comments, and advice regarding my problem.

---

### Post by Brandel Valico on 2011-03-14
Glad it worked for you. 

Don't forget to mark the thread Solved. so others know your issue is resolved and are able to locate the fix for this issue easier.

---

