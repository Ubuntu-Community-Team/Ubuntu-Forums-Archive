---
title: "Keyboard Layout Question"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by dragonwolf on 2009-01-07
Does anyone happen to know the equivilant layout for the Microsoft Wireless Comfort Keyboard 4000 in KUbuntu? While the Generic 104 key does work it does not allow for the added functionality of the keyboard (volume controlls, Internet Favorites, etc.)So I was wondering if there was a layout builtin to kubuntu that would allow this or is there a driver file somewhere that I could download for this.

---

### Post by kebes on 2009-01-09
-There is a program called "[Gizmo Daemon]("http://gizmod.sourceforge.net/")" which is designed for getting various input-output devices working. It's [in the repositories]("http://packages.ubuntu.com/search?keywords=gizmod&searchon=names&suite=intrepid&section=all") under the name "gizmod", so you can install it easily. Gizmo Daemon recognizes many media keyboards, so it might "just work" after installing.

-Another program called hotkeys can be used to map those "special keys" to specific functions. I've never used it myself, but [this looks like a decent explanation]("http://linux.omnipotent.net/article.php?article_id=12340").

-xbindkeys might be a another way to manually control the mapping. Again, I've never used it, but [here's an explanation]("http://www.howtoforge.com/linux_multimedia_keyboard").

-It's somewhat complicated, but you can manually remap keys on your keyboard, which can be used to assign keys that are not being recognized. See [this post]("http://ubuntuforums.org/showpost.php?p=2115845&postcount=2") for some information, or [this page]("http://cweiske.de/howto/xmodmap/allinone.html"). Basically you can use your media keys as shortcuts for various actions (e.g. set the "home" key as the keyboard shortcut for launching Firefox).

-A program called LIRC, designed for configuring remote controls, can also be used to define actions for various key signals. It does require a decent amount of configuration to get it right, however.


I'm not sure which approach will work for your keyboard. Good luck.

---

