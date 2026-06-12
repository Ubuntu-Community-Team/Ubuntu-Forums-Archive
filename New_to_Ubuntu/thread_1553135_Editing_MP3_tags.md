---
title: "Editing MP3 tags"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by Dobbie03 on 2010-08-14
In Windows you can edit the "properties" or the tags of mp3 files with out a program, is that possible to do in Ubuntu?  If so what do I use to do this?

---

### Post by Vaphell on 2010-08-14
by default no, because it's a proprietary format installed separately (patent issues) and it would be somewhat strange to support the manipulation of a formats that are not there right off the bat (though it could and even should be done already no matter what, at least in form of a braindead in use plugin). It's kind of possible though with nautilus addon which can add custom options to the context menu. Some kind of external id3 editor is required, but it's invoked directly from your custom 'edit mp3 info' option you can add for mp3 files

how to achieve that
```
sudo apt-get install nautilus-actions kid3-qt
nautilus-actions-config-tool
```

create new entry 'Edit mp3 info'
command tab: command kid3-qt, parameters %f
conditions tab: *.mp3; *.MP3;
only for files

it should appear in right-click menu of mp3 files after nautilus restart.

---

### Post by Dobbie03 on 2010-08-14
Excellent.  Thanks very much!

---

### Post by void.tag on 2011-11-18
hi

just a quick add : parameter must be %d/%f

i tried the %f and it didn't work for me.

cheers

---

### Post by xnixan on 2012-08-07
> **Vaphell said:**
> by default no, because it's a proprietary format installed separately (patent issues) and it would be somewhat strange to support the manipulation of a formats that are not there right off the bat (though it could and even should be done already no matter what, at least in form of a braindead in use plugin). It's kind of possible though with nautilus addon which can add custom options to the context menu. Some kind of external id3 editor is required, but it's invoked directly from your custom 'edit mp3 info' option you can add for mp3 files

how to achieve that
```
sudo apt-get install nautilus-actions kid3-qt
nautilus-actions-config-tool
```

create new entry 'Edit mp3 info'
command tab: command kid3-qt, parameters %f
conditions tab: *.mp3; *.MP3;
only for files

it should appear in right-click menu of mp3 files after nautilus restart.

Many thanks to you :)

---

