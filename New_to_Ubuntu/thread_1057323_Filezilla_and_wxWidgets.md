---
title: "Filezilla and wxWidgets"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by lavadisco on 2009-02-01
So, for quite awhile now Filezilla has had a problem displaying fonts when using a dark theme in Ubuntu (here, 8.10). I heard a rumor that the problem was fixed in FZ 3.1.6, so I grabbed it. Unfortunately the issue is not fixed for me, apparently I need to update my wxWidgets according to this thread I started on Filezilla forums:

[http://forum.filezilla-project.org/viewtopic.php?f=1&t=9427](http://forum.filezilla-project.org/viewtopic.php?f=1&t=9427)

Unfortunately I'm having a hard time moving forward with this guy's instructions. I don't know which wxGTK file I'm supposed to download and install from the very long list that is linked to. 

If anybody can offer any simpler instructions, I'd be very grateful.

---

### Post by snova on 2009-02-01
The last post indicated you needed the absolute latest, so...

At the bottom of the wxWidgets download page ([http://wxwidgets.org/downloads/](http://wxwidgets.org/downloads/)) is a Daily Snapshot link. It's an FTP site, and the link I think you need is this:

[http://biolpc22.york.ac.uk/pub/Daily_HEAD/wxGTK.tar.bz2](http://biolpc22.york.ac.uk/pub/Daily_HEAD/wxGTK.tar.bz2)

Building from source isn't always easy, but have a look in README or INSTALL (hoping they exist).

---

### Post by lavadisco on 2009-02-01
Thank you very much!

---

