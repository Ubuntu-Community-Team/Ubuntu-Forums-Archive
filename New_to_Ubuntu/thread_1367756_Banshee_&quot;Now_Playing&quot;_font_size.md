---
title: "Banshee &quot;Now Playing&quot; font size"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by humphreybc on 2009-12-29
Is there any way to change it? I've looked in gconf but I don't think there's an entry there for it.

It's really cool for parties to show the song that's playing, but unfortunately the text is too small to read on my 1080P 24" monitor unless you're right up close.

---

### Post by LuisGMarine on 2009-12-30
I tried googling some stuff for you, but my search returned nothing.  My best guess and advice to you would be to find out where banshee installs its extentions.  Once you find that location, look for the one named "Notification Area Icon" and open up what ever xml file.  

If you can find that file and post the contents in here I would be more than glad to help you try and hack it to get some results.

---

### Post by humphreybc on 2010-01-23
Hmm I had a look but I couldn't find it at all. :S

---

### Post by Mornedhel on 2010-01-23
I am not familiar with Banshee, but does it use libnotify for its notifications ?

If so, you're probably out of luck. libnotify uses the system font size (principle of least configuration strikes again).

---

### Post by humphreybc on 2010-01-23
Banshee does use the notification system for notifications, yes. But this is not what I want to change.

In Banshee you can go to "Now Playing" and it shows the album cover and some text, then if you hit F it makes it fullscreen. This is what I'd like to change :)

---

### Post by LuisGMarine on 2010-01-23
Try asking one of the developers.  Maybe they can be of further assistance.  They have a bunch of good guys working on that project, all very helpful.

---

