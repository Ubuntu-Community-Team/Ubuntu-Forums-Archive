---
title: "changing icon size in 9.10"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by flopwich on 2009-11-21
I've read a number of posts about changing the icon size, all of which refer to going to Edit.Preferences in Nautilus and changing the zoom size on the icons.  That works for changing the icon size I see in the File browser, but it does not change the size of the icons on the desktop.  I've also read that you can right-click an icon and get a menu to allow you to stretch the icon, which doesn't work at all on the desktop, apparently.

How can I shrink the icon sizes on the desktop?  On my little nine-inch netbook screen, they're just way too big and way too far apart.  It takes four mouse clicks to get from the top to the bottom of the System screen, for example.

Also, the Edit.Preferences dialog box in Nautilus is too tall for the window, so that I can't see the bottom of it and there's no way for me to reach the bottom to change the size so it'll fit.

TIA for any help.

---

### Post by emigrant on 2009-11-21
i think the best thing you have to do is to choose a higher resolution like 1024x768
i think you are having 800x600 ATM

---

### Post by flopwich on 2009-11-22
[FONT=Arial][/FONT]My screen resolution is 1024 x 600, which is the highest resolution the screen can display.

---

### Post by Dennis N on 2009-11-22
The zoom level for the icons can be less than 100%

```
File Manager > Edit > Preferences > Icon View Defaults > Default Zoom Level
```

select 33%, 50%, or 66% whichever works out best.

---

### Post by flopwich on 2009-11-22
I don't think I've got the point across.  The changes listed above all work within the File Manager, but what I'm talking about is the first screen you see when you start the Ubuntu 9.10 Netbook Remix.  It shows you these HUGE icons, big enough for the nearly blind, it looks like, spaced widely apart, and the same holds for each of the menu options you can select from there. See the attached picture for an idea of what I'm talking about.

None of the changes listed above have any effect on those icons, and I'd like to be able to shrink those things to about a quarter their current size so it doesn't take so many clicks to navigate a screen.

---

### Post by Dennis N on 2009-11-22
Well, that must be something specific to UNR. Just assumed things would work the same as standard Ubuntu. I just checked this in Karmic and the desktop icons (and thumbnails) do shrink.

---

### Post by pi.boy.travis on 2009-11-22
I don't think this is possible.  I can't even find anything in GConf. . .  The huge icons are by design, so that the display works well on the largest number of possible netbook displays and resolutions, but there really should be a way to change the size. . . 

I'll keep looking, but if it is really bugging you, I would file a bug report in Launchpad.

---

### Post by flopwich on 2009-11-22
Thanks to both of you.  Knowing that the "grown-up" sized version does have this feature is reassuring.  I was beginning to wonder if there was something I was doing wrong that I couldn't make this happen.:p

I'll take your advice and file a bug report, although it's not really a "bug", I suppose.  It would help to use the screen much more efficiently if I could shrink the icons, though.  Screen real estate is at a premium on these dinky little things.

---

### Post by flopwich on 2009-11-22
Umm...could you provide some minimal level of instruction on where I start to enter a bug complaint?  I searched Google to find a site for Launchpad, but it looks like it's designed for programmers who are working on open source projects, with no obvious way to enter a bug report.  Where does one start?

Thanks.

---

### Post by Dennis N on 2009-11-22
**Reporting Bugs:**

There is a sticky how-to thread here:

[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

Ubuntu Bug Department is here:

[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

### Post by flopwich on 2009-11-23
Thank you.

---

