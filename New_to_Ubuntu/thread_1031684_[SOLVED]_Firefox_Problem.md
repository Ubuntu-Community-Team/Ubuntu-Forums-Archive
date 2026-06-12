---
title: "[SOLVED] Firefox Problem"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by bigal1932flying on 2009-01-05
Tried to import my Bookmarks from a previous version of Ubuntu by replacing the "profiles.ini" file. Now when I try to open Firefox I receive the following message:
"Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."
I cannot see anything to close and restarting makes no difference.
Does anyone know the reason for this?

---

### Post by Copernicus1234 on 2009-01-05
Your firefox bookmarks are stored in ~/.mozilla/firefox/<randomstring>.default/bookmarks.html.

The profile.ini has nothing to do with bookmarks. For me, it contains:

[General]
StartWithLastProfile=0

[Profile0]
Name=default
IsRelative=1
Path=hfp1ddhe.default
Default=1

---

### Post by Toshibawarrior on 2009-01-05
> **bigal1932flying said:**
> Tried to import my Bookmarks from a previous version of Ubuntu by replacing the "profiles.ini" file. Now when I try to open Firefox I receive the following message:
"Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."
I cannot see anything to close and restarting makes no difference.
Does anyone know the reason for this?

As far as I know the profile.ini file is not needed to reload your preferences/bookmarks...you have to copy all of the contents of "XxXxXxXx.default" folder inside the profile folder of firefox (home/.mozilla/firefox/XxXxXxXx.default) into the same location on your new firefox install.

Try going to a Terminal and type:

```
killall firefox
```

But as I said, I never use the "ini" file...I just copy all of the contents of that folder and paste them on the same folder of a new install.

If I wasn't clear enough let me know ;)!

---

### Post by bigal1932flying on 2009-01-06
Didn't have to run "killall firefox" after a few startups Firefox just worked.
Thanks for your help.

---

### Post by GeoFighter on 2009-01-12
Just what I needed! Thanks!

---

