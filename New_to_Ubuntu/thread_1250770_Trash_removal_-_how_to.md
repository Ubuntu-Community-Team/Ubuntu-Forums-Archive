---
title: "Trash removal - how to?"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by texla on 2009-08-26
Seems I get my tutorials backwards or something.  I found out from GParted that I have 54GB of space being used by my Home partition (in one week of use, that seemed a bit large) so I found that through Nautilus I could access my backup folders and see if the files were there. That's where I found 44 GB worth of backups from Sbackup (that sbackup wouldn't even recognize but whatever).  So I sent them to trash where they never showed yup.  I have now learned that they are probably in a root Trash bin.  So I've tried every tutorial and how-to I can find and nothing seems to let me access the root trash folder where they apparently reside.  

GKSUDO Nautilus does not let me access this Trash - and commands like: sudo rm -rf  [FONT=Trebuchet MS][COLOR=DimGray]~/.local/share/Trash/*[/COLOR][/FONT] do nothing.  I'm stumped but I would like to free this space up to do some repartitioning.

Any one have any help for trash removal or space clearing?

---

### Post by nandemonai on 2009-08-26
If the old files were moved to root's trash then they should be in /root/.Trash or something similar.

---

### Post by texla on 2009-08-26
> **nandemonai said:**
> If the old files were moved to root's trash then they should be in /root/.Trash or something similar.
Maybe so - but when I try to click on the trash folder from the browser in Nautilus (which I think is the root, no?) - I can't even open it to see.  Not sure what to do but those 44GB of backups are somewhere and they need to go away...

just tried this and it said: sudo: /root/.Trash: command not found

---

### Post by tuxxy on 2009-08-26
Its at /root/.local/share/Trash/files, open terminal and run

```
gksudo nautilus /root/.local/share/Trash/files
```

---

### Post by texla on 2009-08-26
> **tuxxy said:**
> Its at /root/.local/share/Trash/files, open terminal and run

```
gksudo nautilus /root/.local/share/Trash/files
```
that did it - Root Trash is all gone - thanks!

---

### Post by tuxxy on 2009-08-26
No problem :D

---

