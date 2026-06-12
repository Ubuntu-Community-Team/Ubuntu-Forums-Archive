---
title: "How do get ls to print full path to file"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by CaptainMark on 2011-04-11
For a script id like the output from ls to print the full path of files found, is there a way to do this?
So I mean i want to be able to run ls from my home folder but instead of getting the output of Documents, Music, Pictures etc etc. if it could print /home/mark/Documents, /home/mark/Music etc etc.

---

### Post by deathadder on 2011-04-11
You can't as far as I know, I tend to use find when I want the absolute path for files. So everything in the current directory would be:
```

find `pwd` -maxdepth 1

```
If you want a recursive listing simply remove -maxdepth 1. You can use -iname to search for particular file types:
```
 find `pwd` -iname '*.jpeg'
```

[http://www.devdaily.com/unix/edu/examples/find.shtml](http://www.devdaily.com/unix/edu/examples/find.shtml)
[http://linux.about.com/od/commands/a/blcmdl1_findx.htm](http://linux.about.com/od/commands/a/blcmdl1_findx.htm)
[http://linux.about.com/od/commands/l/blcmdl1_find.htm](http://linux.about.com/od/commands/l/blcmdl1_find.htm)

---

### Post by CaptainMark on 2011-04-11
aah i was afraid of that, my script is going to need some real reworking to still run with find, i had a reason not to use find to start with but i cant remember why now,

---

### Post by profeta81 on 2011-04-11
sorry, but it's not very clear what exactly you want to do but, for what I understood, yeah, I would use find as well... and btw, keep in mind that if you have many directories and files in your home, find may take _very_ long time to execute so try to restrict the search as much as possible (either by specifying a maxdepth or by using find in subdirectories of your home)

cheers ;)

---

