---
title: "How do I set Sound-Juicer as default ripper?"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by MockY on 2008-12-03
I would like to make sound-juicer the default application to open when inserting a CD and at the same time keep VLC as default application when a DVD is inserted.
How do I go about to do this?

**EDIT:** I though Preferred Applications controlled Video Media as well...but it doesn't. I changed the Multimedia Player on the Multimedia tab and it opens just fine when a CD is inserted.

BUT, how do I change the default video player from Totem to VLC?

---

### Post by mc4man on 2008-12-04
You didn't say whether your running 8.10 or 8.04.
For both you might as well add file management to your preferences menu.

Right click Applications -> edit menus and highlight preferences. On the right side enable 'file management'. Close out and you'll find useful stuff in System -> preferences -> file management.

If your running 8.10 in file management -> media you'll be able to set vlc as default (autorun player) for Dvd Video.

For 8.04 there are a couple of ways. This is the simplest, note you only use this method once, see link below.

Also for 8.04 while your in 'edit menus' also highlight 'Sound & Video, right click on vlc -> properties and change command to this. (better for autoplay and overall in general

```
vlc %f
```

[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

---

