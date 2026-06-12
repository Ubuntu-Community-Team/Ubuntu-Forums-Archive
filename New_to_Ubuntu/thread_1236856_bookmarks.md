---
title: "bookmarks"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by necromonger on 2009-08-10
hi all,
      how do i get my book marks from vista to ubuntu?

---

### Post by Schendje on 2009-08-10
Firefox's bookmarks on Vista are at "C:\Users\username\AppData\Roaming\Mozilla\Firefox\Profiles\profilename\"

You should be able to copy bookmarks.html to "/home/user/.mozilla/firefox/profilename/". That should work.

You can also copy the entire profile folder, I believe.

Another option would be to fire up Vista and export the bookmarks first, then import it again on Ubuntu.

---

### Post by necromonger on 2009-08-10
ok, thank you.

---

### Post by lovinglinux on 2009-08-11
> **Schendje said:**
> Firefox's bookmarks on Vista are at "C:\Users\username\AppData\Roaming\Mozilla\Firefox\Profiles\profilename\"

You should be able to copy bookmarks.html to "/home/user/.mozilla/firefox/profilename/". That should work.

You can also copy the entire profile folder, I believe.

Another option would be to fire up Vista and export the bookmarks first, then import it again on Ubuntu.

The bookmarks.html file does not contain your bookmarks. It holds the default bookmarks added when you first launch firefox or create a new profile. The user bookmarks are in **places.sqlite**, which is a database file. Just copy that and you get all your bookmarks.

You can also copy the **.json** files from **bookmarkbackups** folder, just in case something goes wrong.

You can copy your entire profile indeed, but I don't recommend that, considering that some extensions are OS dependent and some database files might get corrupted in the process. Firefox will check extension compatibility upon start, but since FF profiles get easily corrupted, it would be better to start from fresh. I'm not saying it won't work. Actually I did it myself when switched to Linux, but it is better to use a clean profile.

---

### Post by mapes12 on 2009-08-11
> **necromonger said:**
> hi all,
      how do i get my book marks from vista to ubuntu?
This is what I did:

1. Install the windoze version of Firefox on you windoze PC
2. Have Firefox automatically import you IE bookmarks
3. Install the Xmarks addon for Firefox (Bookmark sync application) on you windoze PC
4. Go to your UBU machine. In Firfox install Xmarks addon. Have Xmarks sync with your account on the Xmarks server
5. Job done in just a few GUI mouse clicks.

You can then have your up to date bookmarks on any machine you like with the Xmarks addon in Firefox. I have 3 machines that just sysnc with the Xmarks server each time I launch Firefox. Change my bookmarks on one machine and the rest follow via a sync at startup.

---

