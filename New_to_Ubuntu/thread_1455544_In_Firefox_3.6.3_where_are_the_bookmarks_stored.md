---
title: "In Firefox 3.6.3 where are the bookmarks stored?"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by bwallum on 2010-04-16
In Firefox 3.6.3 where are the bookmarks stored? 

I have found /home/USER/.mozilla/firefox but not sure where the bookmarks file is. There is a folder called 'bookmarksbackup' and a number of .json files within it.

Are these the files that Firefox uses to load up the bookmarks toolbar? Is it just a question of using the latest backup file?

---

### Post by Didius Falco on 2010-04-16
The file that contains your bookmarks is places.sqlite in your xxxxxxxx.default directory.
 
For more info, go here:

[http://support.mozilla.com/en-US/kb/profiles](http://support.mozilla.com/en-US/kb/profiles)

Regards,

Didius

---

### Post by lovinglinux on 2010-04-16
What do you want to do with that file?

If you want to open it, you will need a sqlite manager. I recommend [SQLite Manager](https://addons.mozilla.org/en-US/firefox/addon/5817) extension for Firefox.

---

### Post by bwallum on 2010-04-17
Thanks all, I want to save my bookmarks to a USB memory stick and then re-install after a dist-upgrade.

---

### Post by coffeecat on 2010-04-17
> **bwallum said:**
> Thanks all, I want to save my bookmarks to a USB memory stick and then re-install after a dist-upgrade.

You shouldn't need to backup and restore the bookmarks for a dist-upgrade - the bookmarks should remain in place. But if you do need to backup and restore, one way is in Firefox: Bookmarks > Organise bookmarks > Import and Backup > Export HTML. And then Import HTML on your new installation.

One slight quirk is that any bookmarks/bookmark-folders on your bookmarks toolbar will be found in a folder called 'Bookmarks Toolbar' inside Bookmarks menu when you first re-import. But it's a simple job to select all and move to the bookmarks toolbar.

---

### Post by lovinglinux on 2010-04-17
> **coffeecat said:**
> You shouldn't need to backup and restore the bookmarks for a dist-upgrade - the bookmarks should remain in place. But if you do need to backup and restore, one way is in Firefox: Bookmarks > Organise bookmarks > Import and Backup > Export HTML. And then Import HTML on your new installation.

One slight quirk is that any bookmarks/bookmark-folders on your bookmarks toolbar will be found in a folder called 'Bookmarks Toolbar' inside Bookmarks menu when you first re-import. But it's a simple job to select all and move to the bookmarks toolbar.

You could also use FEBE extension to backup your entire profile, use Xmarks or Mozilla Weave to sync the bookmarks....see [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by Easy Limits on 2010-04-17
You can export your bookmark file inside of Firefox to an external storage device for safe keeping.  Go to Bookmarks -> Organize Bookmarks.    I do this all the time.  Then I import the bookmark file as needed to my other computers.

---

### Post by bwallum on 2010-04-17
ah, penny dropped eventually, thanks everyone. 

Summary:
The .json files can be restored in Firefox through Bookmarks>Organise Bookmarks>Import and Backup>Restore

They are to be found in /home/USER/.mozilla/firefox/********.default/bookmarkbackups
(the ******** will be a mix of lower case characters and numbers)

Great stuff and thanks to everyone again.

---

