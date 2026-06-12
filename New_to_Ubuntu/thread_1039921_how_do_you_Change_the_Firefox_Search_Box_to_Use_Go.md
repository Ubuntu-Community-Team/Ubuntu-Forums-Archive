---
title: "how do you Change the Firefox Search Box to Use Google's New Favicon?"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2009-01-15
?

---

### Post by Lod on 2009-01-15
I don't, I find the new icon just plain ugly.

---

### Post by shiningkenmonster on 2009-01-15
well here is the link for windows firefox. but no help with ubuntu's firefox. is there a command line to do this too?

[http://lifehacker.com/5130910/change-the-firefox-search-box-to-use-googles-new-favicon](http://lifehacker.com/5130910/change-the-firefox-search-box-to-use-googles-new-favicon)

---

### Post by mc4man on 2009-01-15
Very simple
Go here and right click on link "save link as"
That will download 'google.xml' to your desktop

[http://mozillalinks.org/wp/2009/01/update-firefox%E2%80%99s-search-bar-with-new-google-favicon-again/](http://mozillalinks.org/wp/2009/01/update-firefox%E2%80%99s-search-bar-with-new-google-favicon-again/)

Then search in filesystem for google.xml and replace with the new one. 

Should be in /usr/libs/firefox-addons/searchplugins

Tested and works fine.

Edit: I would copy the old one somewhere before replacing in case you want to go back to orig.

---

