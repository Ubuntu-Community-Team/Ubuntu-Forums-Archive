---
title: "Why does Xubuntu change my background everytime it restarts?"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by frustratednerd on 2010-06-09
hi, i'm a new linux user who just transitioned over from windows and just recently installed xubuntu. so far... my experience has not been pleasant. i've been experiencing many issues, such as... xubuntu changing my background every time i restart it, to the default background. please help... i'm very close to throwing this computer out the window.

---

### Post by mesuhas_sit on 2010-06-09
Hi welcome to Linux and Ubuntu forums..
 
Looks like this problem was the same i had when i switched over from Windows to Ubuntu. Is your wallpaper file located in the home folder or other drive which you mounted to access it?
 
If it is on a mounted drive or a folder then at startup this will not be mounted. So what you can try is to copy that wallpaper to the pictures folder in your home directory. 
 
Give some details of your other problems many here can help you

---

### Post by 4Orbs on 2010-06-09
Maybe because the background you are using is located in a folder that is not on your xubuntu partitions. Just a guess. The easiest way to make backgrounds persistent and available to all users is to copy the image, using administrator rights, and paste into the default folder for backgrounds. Here's how. First open a terminal and enter this command:
```
gksudo thunar
```
which will open your file manager as administrator (root user). Then navigate to the folder where your desired background is now stored (Is it on your Windows partition somewhere?) and copy the image. Then navigate to the Xubuntu (File System) /usr/share/xfce4/backdrops folder and paste the image there. Now close the file manager and terminal. Open the Xfce4 Settings Mgr, click on the Desktop icon and your background should now appear in the list. You can select it, and it will still be there at your next login.

If it isn't there next login... open the Xfce4 Settings Mgr, click on "Sessions and Startup" and tick the option to "Automatically Save this Session on Logout". Then select your wallpaper again from the list and it will be there next time.

---

### Post by XubuRoxMySox on 2010-06-09
> **4Orbs said:**
>  The easiest way to make backgrounds persistent and available to all users is to copy the image, using administrator rights, and paste into the default folder for backgrounds.

Exactly right! I put my entire collection of wallpapers in **/usr/share/xfce4/backdrops** and changing them is a snap from the right-click-anywhere-on-the-desktop menu.

Enjoying it,
Robin

---

### Post by frustratednerd on 2010-06-09
alright, thanks for the help everyone.

here are some things i was wondering how to do on xubuntu that i'm used to doing on windows:

1. some sort of 'start -> run' function that i could use to access files instead of having to click on 'home' or 'file system' every time i want to access a file/folder

2. creating shortcuts to files/folders on my desktop

3. is there any way to control what starts up with xubuntu? i noticed that pidgin and firefox automatically start up when xubuntu starts.

Also, some other questions:

1. What's better to use? Synaptic or Ubuntu Software Center?
2. is there something similar to 'control panel' in xubuntu? if so, how do i access it?

---

### Post by JKyleOKC on 2010-06-09
> **frustratednerd said:**
> alright, thanks for the help everyone.

here are some things i was wondering how to do on xubuntu that i'm used to doing on windows:

1. some sort of 'start -> run' function that i could use to access files instead of having to click on 'home' or 'file system' every time i want to access a file/folder

2. creating shortcuts to files/folders on my desktop

3. is there any way to control what starts up with xubuntu? i noticed that pidgin and firefox automatically start up when xubuntu starts.

Also, some other questions:

1. What's better to use? Synaptic or Ubuntu Software Center?
2. is there something similar to 'control panel' in xubuntu? if so, how do i access it?You can set shortcuts in Thunar to go directly to a folder. First navigate to the parent directory, then select the desired folder and drag it to the lower left area of the Thunar window. Unlike Windows, this doesn't actually move the folder; instead it creates a shortcut in that area. For instance, I have set up such shortcuts to /etc and /var/log on my systems; they appear as just "etc" and "logs" in the shortcut area (you can right-click on the shortcut and rename it to what you want it to say).

For the start-->run situation, you can create launcher icons in either of thunar's panels. Right-click on the panel area and select "Add new item" to get started, then fill in the blanks of the resulting dialog. This took a few days for me to get used to but I now find it as easy to use as the old Windows desktop cluttered with shortcut icons.

In the applications menu there's a "Settings" item; selecting it gets a submenu that starts with "Settings Manager" and selecting that brings up a new window with a number of choices, the first of which is "Autostarted applications." This Settings Manager is to closest thing to the Control Panel that I've found, and the "Autostart" icon lets you select what starts automatically when you log in.

Hope this helps you some. Much of the information here in the forums is for Ubuntu, and Xubuntu has a few differences, but the general principles are the same...

I prefer using Synaptic for downloading and installing things, but it's mostly a matter of personal preference.

---

