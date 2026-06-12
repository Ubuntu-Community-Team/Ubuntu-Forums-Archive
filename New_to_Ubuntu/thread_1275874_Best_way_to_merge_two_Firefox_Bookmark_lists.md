---
title: "Best way to merge two Firefox Bookmark lists?"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by swarup on 2009-09-26
I have two computers, each with their own Firefox bookmarks. I would like to merge the two lists, eliminating duplicates in the process, and have brought one computer's "firefox" folder (home->moxila->firefox) and pasted it onto the desktop of my other computer. What is the process from here?

I just need to have the new merged list functional on my new computer.

---

### Post by swarup on 2009-09-26
I found this post on [another]("http://www.democraticunderground.com/discuss/duboard.php?az=view_all&address=105x4224576") forum:

> Bookmarks Synchronizer is a Mozilla Firefox extension that let you connect to an FTP server and synchronize your bookmarks that are stored in an XML file. Setup is easy; just write in your FTP server address, username, password and a name for the XML file (by default called xbel.xml).

To start, press Upload to create the file on the server and set if you want to automatically download the file on startup or upload it when you close your browser. Allows one to merge bookmarks files. (eg between desktop and laptop)

It sounds very good-- but it will only work if both computers are functional! :( My old computer is broken, and so I had to get its firefox folder and paste it on my new computer's desktop, as described above. That is, for me the work will have to be done using one computer only.

---

### Post by Ray716 on 2009-09-26
since your computer is dead.. you might have to just add everything in there manually... But when that is done, try Xmarks, it is a great way to save and store all your favorite bookmarks and has features to access it at work, or even from a public computer. I enjoyed it, and found it very useful after i switched to Ubuntu and only had to re-install Xmarks from the Modzilla addons, then synchronize my book marks.. very easy.

---

### Post by swarup on 2009-09-26
> **Ray716 said:**
> since your computer is dead.. you might have to just add everything in there manually...

ok, if there is no other way, then I won't mind even if I have to do so. So when one opens the firefox bookmark file, each saved entry looks like the following:

> description","flags":0,"expires":4,"mimeType":null,"type":3,"value":"[Archive]  How To: Exit  X-Server Absolute Beginner Talk"}],"type":"text/x-moz-place","uri":"http://ubuntuforums.org/archive/index.php/t-309787.html","charset":"ISO-8859-1"},{"index":12,"title":"How to get rid of being asked my password - Ubuntu Forums","id":96,"parent":2,"dateAdded":1241711933997030,"lastModified":1241711934009258,"annos":[{"name":"bookmarkProperties

Does one just copy-paste this entry into the new computer's firefox bookmarks file, and it will be bookmarked the same as it was in the old computer? i.e. the listing for it will appear the same in my new bookmarks menu, and when clicked on it will go to the referenced site?

---

### Post by tahitiwibble on 2009-09-26
Absolutely! Xmarks extension to Firefox. It's great.

---

### Post by oldfred on 2009-09-26
If you go to bookmark, organize bookmarks you can import a html file. You can also restore a file. Restore will probalby replace you current so you could export your current to html, restore you other computer and import you saved html. You will have duplicates that you have to manually edit.

The file is now sqlite so it may be possible to edit it from the sqlite browser?

---

