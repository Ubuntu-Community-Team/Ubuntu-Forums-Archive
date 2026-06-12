---
title: "Change log in screen background"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by Genesis3 on 2009-07-21
Does anybody know how to change the background on the log in screen in Kubuntu 9.04? When I use Login Manager the "Background" tab tells me "The background cannot be configured separately in themed mode"

---

### Post by swoll1980 on 2009-07-21
You really can't change the backround on it's own. It's the theme it's self that is changed. If you go into the theme directory you can change the back round of that particular theme, but I don't know exactly how those work.

---

### Post by Sxeptomaniac on 2009-07-21
You can turn off the themed mode by going to the Login Manager (it's under the Advanced tab of the System Settings).  On the first tab, there's a checkbox labeled "Use themed greeter".  Uncheck it, and you can chage the background manually.

On the other hand, you can download themes from [kde-look.org](http://www.kde-look.org/index.php?xcontentmode=40x41&PHPSESSID=5a389ae219027f38a215dc8c9c1d2578) manually.  Untar them (right click and choose "Extract archive here"), then copy them to the KDM theme folder, which should be /usr/share/kde4/apps/kdm/themes

You'll need root permissions to copy to that folder, so use the terminal command ```
sudo cp -r <theme folder> /usr/share/kde4/apps/kdm/themes
```

After that, it should show up in the Theme tab of the Login Manager control panel.

---

### Post by Genesis3 on 2009-07-21
When I use that command in the Terminal it tells me that the directory doesn't exist:confused:

---

### Post by Sxeptomaniac on 2009-07-21
> **Genesis3 said:**
> When I use that command in the Terminal it tells me that the directory doesn't exist:confused:

Use Dolphin to check nearby directories.  It's probably near there, possibly in /usr/kde/kde4/share/apps/kdm/themes or /usr/kde4/share/apps/kdm/themes.  It could even be under your home directory, under ~/.kde/share/apps/kdm/themes

---

### Post by Genesis3 on 2009-07-21
Neither the Terminal or even Dolphin can find any of those directories :S

Dolphin however can find the directory in this code but the Terminal fails to detect it
```
sudo cp -r <theme folder> /usr/share/kde4/apps/kdm/themes
```

---

### Post by Sxeptomaniac on 2009-07-22
> **Genesis3 said:**
> Neither the Terminal or even Dolphin can find any of those directories :S

Dolphin however can find the directory in this code but the Terminal fails to detect it
```
sudo cp -r <theme folder> /usr/share/kde4/apps/kdm/themes
```

So when you go to /usr/share/kde4/apps/kdm/themes with Dolphin, it's there, but it says it's not when you attempt to copy a theme folder using the terminal?  I'm not sure why that would happen, except due to a possible typo.

The alternative is to try and start a file manager in root mode, though I've had mixed success at it.  Dolphin is the usual file manager.  I tried the KDE root command without success (kdesudo dolphin), but it did work as ```
sudo dolphin
```

That should allow you to copy folders to the directory.

---

### Post by Zorael on 2009-07-23
You may want to check out the [kdm theme generator](http://www.kde-apps.org/content/show.php/Kdm+theme+generator?content=102760) (and on a semi-related note, the [ksplash theme generator](http://www.kde-apps.org/content/show.php/Ksplash%20theme%20generator?content=104456)). Doesn't look like there are debs available though.

---

