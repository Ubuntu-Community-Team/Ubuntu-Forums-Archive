---
title: "help editing system.reg file - won't save!"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by wiab4355 on 2009-05-31
OK - trying to install Digiguide via Wine

Digiguide support says I have to edit /.wine/system.reg

In Terminal I typed gedit /.wine/system.reg, Terminal showed a bunch of error messages (cannot extract frame etc...) but the text editor then opened OK (although the file was blank). I typed the lines Digiguide support recommended:

[software\\Microsoft\\Windows\\CurrentVersion ] 1102337138
"Registered Owner"="wiab4355"

and tried to save it. An error message saying "Could not find the file /.wine/system.reg
Please check that you have typed the location correctly and try again.

---

### Post by nandemonai on 2009-05-31
> **wiab4355 said:**
> OK - trying to install Digiguide via Wine

Digiguide support says I have to edit /.wine/system.reg

In Terminal I typed gedit /.wine/system.reg, Terminal showed a bunch of error messages (cannot extract frame etc...) but the text editor then opened OK (although the file was blank). I typed the lines Digiguide support recommended:

[software\\Microsoft\\Windows\\CurrentVersion ] 1102337138
"Registered Owner"="wiab4355"

and tried to save it. An error message saying "Could not find the file /.wine/system.reg
Please check that you have typed the location correctly and try again.

```
gedit ~/.wine/system.reg
```

The .wine directory exists in your home directory, not in the root of the file system '/'.

---

### Post by coffeecat on 2009-05-31
> **wiab4355 said:**
> gedit /.wine/system.reg


That's your mistake. Gedit is trying to open a file /.wine/system.reg which doesn't exist because there is no folder /.wine in the root of the filesystem. What you want is /home/yourusername/.wine/system.reg, so open a terminal, do not cd into any other folder, and type:

gedit ./.wine/system.reg

or

gedit ~/.wine/system.reg

or

gedit .wine/system.reg

---

### Post by wiab4355 on 2009-05-31
Thanks, but it's still not saving

I think it's saved, but when I open it again the bit that's supposed to have been edited hasn't!

Seems like I'll have to do without Digiguide - damn! One more year left on my subscription!!

---

### Post by CatKiller on 2009-05-31
> **wiab4355 said:**
> Thanks, but it's still not saving

I think it's saved, but when I open it again the bit that's supposed to have been edited hasn't!

You probably don't want to have Wine running while you're playing with its pretend registry.

You can just run regedit if you want to change Wine's pretend registry.

You could also just find the file in the normal file manager window to make sure that you're editing the right file. Ctrl-H will show hidden files, and the file you want is in .wine.

There should be plenty in there. That file stores Wine's pretend HKey-Local-Machine registry entries.

---

### Post by wiab4355 on 2009-06-01
Thanks CatKiller - it worked!

---

