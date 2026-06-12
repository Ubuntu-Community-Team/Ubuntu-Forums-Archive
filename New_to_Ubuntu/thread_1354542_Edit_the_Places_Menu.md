---
title: "Edit the Places Menu?"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by L a r r y on 2009-12-14
I have been experiencing an issue that I would like to solve without having to reinstall from scratch.

I installed Kiwi 9.04, a version of Ubuntu 9.04.  I brought in some backed-up data from my old Ubuntu 8.04, overwriting my /home/user folder.

Kiwi is a version of Ubuntu with some restricted codecs included.

While all my browser and email settings are right there, it did mess up the access to my "Home folder," "Desktop," and Bookmarks, all in the top of the Places Menu.

I have a [thread open in General help]("http://ubuntuforums.org/showthread.php?t=1353910") that lays out what I have discussed already.

But since the issue that I need an answer to is related to these top three entries (and all the expanded bookmarks), with no issues with the computer and CD ROM links in the Places Menu, I wanted to open a new thread on this topic.

It is true that one can open a file browser (as with the Computer entry on the Places Menu) and have access to the bookmarks in the left pane and these can be removed by right-clicking on them, and they can be edited from the Bookmarks menu at the top of the file browser window.

If I remove a bookmark, it is removed from the Bookmarks list in the Places Menu, and if I add a bookmark in the left pane it is added to the Places Menu.

The bookmarks work properly in the left pane of the file browser.

My problem is, after I imported backups from my archive file into the /home/user folder, my Places Menu wants to open these directories in my text editor.

If I delete and then add the bookmark to someplace in the file browser, I have removed and restored it to the Places Menu, but the newly added bookmark wants to open in gedit.

My only solution to this problem has been to wipe the system and re-install from the live CD, then set it all up and then update it for half an hour.

And since I have been just getting a new installation up and going, it has only been a few hours wasted blowing it away and re-installing after I get this issue from my backup archive.

People have asked this post's question repeatedly over the last two years without any resolution.  A search of Google for **ubuntu edit places menu** will show many results but no definitive answers to the question of how to edit the menu.

Now there is an edit-menus option if you right-click on the Applications, Places, System headings on the top panel.  This only allows you to edit the Applications Menu and the Systems Menu contents.  No help there for the Places Menu.

I would like to know what file in my Home Folder is responsible for screwing up the functioning of these top entries above the divider line in the Places Menu.

I have moved .gconf and .gconfd to their respective names.old and restarted the computer.  That recreated these configuration files, but had no effect on this Places Menu opening the directory in my text editor.  These files, which have a dot at the beginning are hidden files in Linux and Unix, and are in the user folder's root.  In other words, /home/user/.gconf.

The move operation is accomplished in the Terminal's command-line as follows:
```
 sudo mv ~/.gconf ~/.gconf.old && sudo mv ~/.gconfd ~/.gconfd.old
```
After running this code, restart the computer, or log out and back in.

Being that I have placed this thread in the Beginner's forum, I have written a fair amount of detail, and there is hopefully some help for others.

---

### Post by skymera on 2009-12-14
You can also edit them using Ubuntu Tweak.

---

### Post by L a r r y on 2009-12-14
> **skymera said:**
> You can also edit them using Ubuntu Tweak.

[[COLOR="RoyalBlue"]Download Ubuntu Tweak[/COLOR]]("http://ubuntu-tweak.com/downloads") and let the default package installer handle it.

Hey, thanks for that tip.  I looked it up in Google and downloaded the version for Ubuntu 9.04.  

With Ubuntu Tweak, I removed the mounted disk partition's icon from the Desktop.  It is still accessible from the Places menu.


I have solved my issue with the Places menu, by not overwriting everything into my /home/user folder from my backup.

I have reinstalled the system and updated it, and then I backed it all up.

I extracted my 8.04 home backup elsewhere and moved only my Firefox, Thunderbird and gftp and copied them here, then I backed-up Home.

The question remains unanswered, however as to what was the cause of all of this trouble, and what is the solution short of reinstalling.  A file in the user's Home folder, amongst the hidden files and folders there.

---

