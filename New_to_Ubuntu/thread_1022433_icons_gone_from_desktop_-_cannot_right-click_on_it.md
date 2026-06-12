---
title: "icons gone from desktop - cannot right-click on it"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by al.adab on 2008-12-26
hello,

please first see my post at
[http://ubuntuforums.org/showthread.php?t=1022326](http://ubuntuforums.org/showthread.php?t=1022326)

although I can now access all my files at home folder, I still don't know how to get my desktop back to normality: 

- the photo I set as wallpaper is still there;
- the icons for the files I had on it are gone;
- no response if I right-click on it;
- the files can still be found at the folder "desktop" at myDocuments (home folder). 

What shall I do? Thanks for your help.

---

### Post by gettinoriginal on 2008-12-26
Depends how you set the photo for your desktop.  If you did it through comiz, then the photo is a decoration and "covers" your desktop as a shade covers a window.  Just to see, use the default in preferences, appearance, and see if that brings back your icons.

---

### Post by drs305 on 2008-12-26
If that doesn't work, it could be you have 'turned off' your desktop. In this case, run the following command to turn it back on:
```

gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 'true'

```

---

### Post by crf on 2008-12-26
I had a similar problem once. 

[http://ubuntuforums.org/showthread.php?t=657106](http://ubuntuforums.org/showthread.php?t=657106)

My desktop lost its icons. Right-clicking brought up no menu.

What you can try:
Create a new user, as a test, and log in as that user (system menu --> administration --> users and groups). Log in, and see if the new user's desktop works ok. If it does, then it is something particular to the user account you normally use. 

Try deleting (you may wish to make backups first) the .gconf and .gconfd files in your original profile, then logging back in. I think you'll lose whatever desktop customisations you had, and they'll have to be re-created.

You can then delete the user account you used to test.

---

