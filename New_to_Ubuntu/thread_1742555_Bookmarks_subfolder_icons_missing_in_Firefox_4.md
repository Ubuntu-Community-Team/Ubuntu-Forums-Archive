---
title: "Bookmarks subfolder icons missing in Firefox 4"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by tahitiwibble on 2011-04-29
My apologies if this is out of, or in the wrong place, but it took me ages to find a solution to this problem where my folder icons in bookmarks in Firefox 4 had disappeared. A very good man has the solution here; [http://www.fedoraforum.org/forum/showthread.php?t=259976](http://www.fedoraforum.org/forum/showthread.php?t=259976)

---

### Post by lovinglinux on 2011-04-29
For future reference, see [Firefox 4 Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247").

---

### Post by powder on 2011-04-29
> **tahitiwibble said:**
> My apologies if this is out of, or in the wrong place, but it took me ages to find a solution to this problem where my folder icons in bookmarks in Firefox 4 had disappeared. A very good man has the solution here; [http://www.fedoraforum.org/forum/showthread.php?t=259976](http://www.fedoraforum.org/forum/showthread.php?t=259976)

Thanks!  I was looking for this. :D

---

### Post by spielball on 2011-04-29
Thank you. I had this problem, too.

According to that forum post, just put the following code in

[SIZE=2]~/.mozilla/firefox/<profile_name>/chrome/userChrome.css[/SIZE]

```
[SIZE=2]@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");
menu.bookmark-item > .menu-iconic-left {
  visibility: visible;
}[/SIZE]
```If there isn't a chrome folder and/or userChrome.css, just create them.

For the newbs (I am one): to see the mozilla folder in your home profile, you have to use shortcut CTRL+H to see hidden folders.

---

### Post by 2541 on 2011-05-02
Thanks for the solution, tahitiwibble. It helped me a lot.

---

### Post by Niva on 2011-05-26
Neither of these solutions has worked for me by the way.  Only the subfolder icons are missing off the bookmarks toolbar in Firefox 4, Ubuntu 11.04x64

---

### Post by lovinglinux on 2011-05-26
> **Niva said:**
> Neither of these solutions has worked for me by the way.  Only the subfolder icons are missing off the bookmarks toolbar in Firefox 4, Ubuntu 11.04x64

Close Firefox, rename the file places.sqlite from your FF profile folder (~/.mozilla/firefox/<profilename>/places.sqlite) to places.sqlite.old. Start Firefox, open the Bookmarks manager (CTRL+SHIFT+O), select "Import & Backup >>> Restore" and select the latest backup to restore your bookmarks.

---

### Post by anand.pathak.sharma on 2013-02-06
> **spielball said:**
> Thank you. I had this problem, too.

According to that forum post, just put the following code in

[SIZE=2]~/.mozilla/firefox/<profile_name>/chrome/userChrome.css[/SIZE]

```
[SIZE=2]@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");
menu.bookmark-item > .menu-iconic-left {
  visibility: visible;
}[/SIZE]
```If there isn't a chrome folder and/or userChrome.css, just create them.

For the newbs (I am one): to see the mozilla folder in your home profile, you have to use shortcut CTRL+H to see hidden folders.
Can confirm (years later and in Firefox 18 after importing my profile from an Windows installation) that this works!

Thanks to the two who posted this!

On the side, I wanna mention that I needed to rename userChrome-example.css to userChrome.css and restart Firefox to see the change.

Cheers!

---

