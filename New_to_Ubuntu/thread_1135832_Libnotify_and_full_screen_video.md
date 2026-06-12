---
title: "Libnotify and full screen video"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-04-24
I'm using Jaunty and whenever someone signs onto pidgin libnotify displays a message.

This is great usually, however, when I'm playing a movie full screen (either with smplayer or vlc) and libnotif displays someone coming online, the screen flickers. This is really irritating. Is there anyway to automatically disable libnotify when I'm playing something full screen.

---

### Post by humphreybc on 2009-08-12
I'd like to know how to disable libnotify entirely, or at least in fullscreen applications.

Whenever I watch a movie, or play fullscreen games, or use Windows XP virtualbox fullscreen and change the volume or brightness etc, the screen will flicker for a few seconds, and in fullscreen video which is really sensitive already due to Compiz, it will often freeze the video and lock up the computer.

I think this is really unprofessional, I think that at least libnotify needs an option to turn it off, or an option to have it disabled under fullscreen applications. Or perhaps have some sort of precedence system where libnotify is told to appear UNDER any fullscreen windows.

Vote for my libnotify solution on brainstorm:

[[IMG]http://brainstorm.ubuntu.com/idea/21034/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/21034/)

---

### Post by gardara on 2009-08-13
Interested in this as well.
Smplayer's "always on top" doesn't fix this but it should (imo).

What I do is that I have configured the libnotify plugin for pidgin so it won't display notifications when my status is set to busy. It's not a great solution but better than nothing.

Maby also pidgin could be configured so it would automatically change your status to busy when playing videos in full screen, if I remember correctly windows live messenger does that.

---

### Post by kansasnoob on 2009-08-13
Well, look at my post #6 here:

[http://ubuntuforums.org/showthread.php?t=1233114](http://ubuntuforums.org/showthread.php?t=1233114)

Of course that involves also changing the update icon (along with frequency), but you can go back to the old style notifications by installing 'notification-daemon (0.4.0-0ubuntu3)' and removing 'notify-osd' which requires the removal of 'ubuntu-desktop'. 

**But, I can't stress strongly enough that removing 'ubuntu-desktop' will break your ability to properly complete a distro upgrade, so it must be reinstalled before trying to upgrade to Karmic!**

---

### Post by kansasnoob on 2009-08-13
BTW I expect notify-osd to get more easily configurable with each new release.

I'd bet on it!

---

### Post by humphreybc on 2009-08-13
Okay, sorry just a quick amendment - it is the package "notify-osd" not "libnotify" that is the root of the problem.

---

