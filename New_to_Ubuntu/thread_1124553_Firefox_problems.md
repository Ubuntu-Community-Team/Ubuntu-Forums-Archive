---
title: "Firefox problems"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by aquascrotum on 2009-04-13
I've hit a fairly major snag with Firefox.

My browsing history and bookmarks have just disappeared into thin air. My Back and Forward buttons no longer work. And a lot of websites dont work - for instance I can't post or use the search facility on the top right in ubuntuforums.org (have had to revert to WinXP and IE for now).

Whats going on!? Have tried uninstalling and reinstalling but problems persist.

---

### Post by nml on 2009-04-13
Not a FF expert, but be sure to reboot your computer (at least once), empty any cache in FF, and you may want to disable or remove your plugins and extensions (they give some folks and systems problems)........then give Google a whirl... found this with which may or may not help..

[http://tinyurl.com/clyyzg](http://tinyurl.com/clyyzg)

mick

---

### Post by RedSingularity on 2009-04-13
Go into your Home Directory.  Display hidden folders by pressing Ctl+H.  Locate the .mozilla folder and delete.  Then start up firefox.  

This will probably solve your other problems but you WILL loose you bookmarks.  I recommend using "Foxmarks" in the future to hold your favorites/Bookmarks safely.

---

### Post by Cresho on 2009-04-13
back up this file before you delete the directory and then you can restore your bookmarks

/.mozilla/firefox/tzafvi6q.default/bookmarkbackups/bookmarks-2009-03-02.json

---

### Post by aquascrotum on 2009-04-13
Deleting the .mozilla folder worked.

My passwords were all synced with Xmarks so no problems there. Only difficulty is lost logins/passwords but that isn't critical.

---

### Post by lovinglinux on 2009-04-13
You can use [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109) extension to schedule regular profile backups and avoid this problem in the future.

With FEBE you can backup your entire profile or just things you need the most, including passwords, permissions, cookies, extensions etc...

---

### Post by moredhel on 2009-04-13
> **lovinglinux said:**
> You can use [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109) extension to schedule regular profile backups and avoid this problem in the future.

With FEBE you can backup your entire profile or just things you need the most, including passwords, permissions, cookies, extensions etc...
Or you could use mozilla weave which is an official extension :)

---

### Post by lovinglinux on 2009-04-13
> **moredhel said:**
> Or you could use mozilla weave which is an official extension :)

Weave is a synchronization tool that requires uploading your data to Mozilla's server. I don't know how it works, but I guess it does not keep a versioning system, so if you damage your profile locally, it could damage the profile on the server too.

FEBE is a backup system that can keep a certain number of backups of your profile, created on a regular interval, so if you damage your profile and a backup, you can still easily recover an older version. Besides, it doesn't require uploading you data to a server.

---

### Post by moredhel on 2009-04-13
> **lovinglinux said:**
> Weave is a synchronization tool that requires uploading your data to Mozilla's server. I don't know how it works, but I guess it does not keep a versioning system, so if you damage your profile locally, it could damage the profile on the server too.

FEBE is a backup system that can keep a certain number of backups of your profile, created on a regular interval, so if you damage your profile and a backup, you can still easily recover an older version. Besides, it doesn't require uploading you data to a server.
The several backups is a plus, but I had this problem before and my weave profile was untouched and fine :) Though that could of been by luck I guess...

---

