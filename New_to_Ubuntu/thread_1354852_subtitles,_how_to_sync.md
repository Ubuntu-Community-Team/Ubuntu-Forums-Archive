---
title: "subtitles, how to sync?"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by beanco on 2009-12-14
I have a movie I want to show to a class. I need the English subtitles to it.

I found the subs and am trying to get them to play. but they are out of sync. Very annoying.

So.... what is the solution? How to get the subs in sync?

Thanks

Robi

---

### Post by ukripper on 2009-12-14
you can try this - [http://www.debuntu.org/2006/04/19/30-how-to-synchronising-subtitles-with-subtitleeditor](http://www.debuntu.org/2006/04/19/30-how-to-synchronising-subtitles-with-subtitleeditor)

---

### Post by beanco on 2009-12-15
> **ukripper said:**
> you can try this - [http://www.debuntu.org/2006/04/19/30-how-to-synchronising-subtitles-with-subtitleeditor](http://www.debuntu.org/2006/04/19/30-how-to-synchronising-subtitles-with-subtitleeditor)

Thanks. Took a look.  Noticed that there was nothing there for Jaunty Jackalope... I will take a further look... 

Rob

---

### Post by ukripper on 2009-12-15
This should work fine with jaunty and karmic as well.

More info on latest version : [http://home.gna.org/subtitleeditor/](http://home.gna.org/subtitleeditor/)

---

### Post by Grenage on 2009-12-15
Failing that (and assuming this is not a movie you will be watching many times), players such as mplayer have the ability to advance or delay the sub timing.

---

### Post by nitstorm on 2009-12-15
VLC Media Player should also be able to sync subs :)

---

### Post by beanco on 2009-12-15
what about doing this from the command line... just wondering how it could be done...

robi

---

### Post by ukripper on 2009-12-15
> **beanco said:**
> what about doing this from the command line... just wondering how it could be done...

robi

mencoder

[http://ohioloco.ubuntuforums.org/showthread.php?t=1155877](http://ohioloco.ubuntuforums.org/showthread.php?t=1155877)

---

### Post by beanco on 2009-12-15
> **nitstorm said:**
> VLC Media Player should also be able to sync subs :)

I was playing it in VLC and the subs were coming way to fast, they were like 15 seconds early or sg...

This is a movie I will be showing 5 or 6 times this week...

Thanks for all the ideas.. I will try the command line stuff and I will try the other movie player 

robi

---

### Post by northern lights on 2009-12-15
> **beanco said:**
> Thanks. Took a look.  Noticed that there was nothing there for Jaunty Jackalope... I will take a further look... 
Rob

*subtitleeditor* is in the repositories.```
sudo apt-get update && sudo apt-get install subtitleeditor
```

---

### Post by beanco on 2009-12-16
Installing it right now. Thanks!

I will try it out...

Robi

---

