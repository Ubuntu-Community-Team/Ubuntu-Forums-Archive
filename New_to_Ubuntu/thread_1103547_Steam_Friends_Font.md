---
title: "Steam Friends Font?"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by efexD on 2009-03-22
I noticed when running steam in wine it worked great but the font for the friends list must not be on linux or something because it makes it very hard to read the names of my friends, when i chat with them the font is different and easy to read. Does anyone know the name of the font it uses? Or a fix?

---

### Post by Xiong Chiamiov on 2009-03-23
Have you installed the msttcorefonts package?

---

### Post by efexD on 2009-03-29
Tryed that. Didn't work.

---

### Post by fatbuttlarry on 2009-12-01
Try this:
[http://fatbuttlarry.blogspot.com/2009/12/steam-friends-font-fix.html](http://fatbuttlarry.blogspot.com/2009/12/steam-friends-font-fix.html)

[SIZE="5"]Steam Friends Font Fix[/SIZE]

Quick fix to read the very small names in steam buddy list running Ubuntu 9.10 and Wine wine-1.1.33 (should work with other versions of Linux and Wine)

Before: [[IMG]http://ubuntuforums.org/attachment.php?attachmentid=138271&stc=1&thumb=1&d=1259699203[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=138271&stc=1&d=1259699206")  After:  [[IMG]http://ubuntuforums.org/attachment.php?attachmentid=138272&stc=1&thumb=1&d=1259699203[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=138272&stc=1&d=1259699206")


[LIST=1]
[*]**Gnome:**
      ```
gedit ~/.wine/drive_c/Program\ Files/Steam/resource/steamscheme.res
```
      **KDE:**
      ```
kate ~/.wine/drive_c/Program\ Files/Steam/resource/steamscheme.res

```
[*]Find the section called **"FriendsSmall"**
      Change
      ```
"tall" "12"
```
      to
      ```
"tall" "13"
```

[*]Find the section called **"FriendsVerySmall"**
      Change
      ```
"tall "12"
```
      to
      ```
"tall" "13"
```

[*]Save the file and restart steam.
[/LIST]


***Note:** This file gets reset after a steam update, so make a copy of it.

***Note:** If you don't use the default dark green theme, find the "steamscheme.res" file in your skins --> resource folder for the appropriate skin.


-Tres

---

### Post by ATL™ on 2009-12-01
you could download the fonts it needs ([https://support.steampowered.com/downloads/1974-YFKL-4947/SteamFonts.zip](https://support.steampowered.com/downloads/1974-YFKL-4947/SteamFonts.zip)) and put them in ~/.wine/dosdevices/c:/windows/Fonts

that usually fixes it for me.

---

### Post by masque7 on 2010-01-04
> **ATL™ said:**
> you could download the fonts it needs ([https://support.steampowered.com/downloads/1974-YFKL-4947/SteamFonts.zip](https://support.steampowered.com/downloads/1974-YFKL-4947/SteamFonts.zip)) and put them in ~/.wine/dosdevices/c:/windows/Fonts

that usually fixes it for me.
This method works.

---

