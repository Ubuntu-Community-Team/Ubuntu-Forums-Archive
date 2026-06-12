---
title: "Installing Conky"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by abeautifulplace on 2009-03-24
(Just following the installation instructions)
When I type
```
zcat /usr/share/doc/conky/examples/conkyrc.sample.gz > ~/.conkyrc
``` 
in the terminal, I get this error:
> gzip: /usr/share/doc/conky/examples/conkyrc.sample.gz: No such file or directory
What am I doing wrong? :(

---

### Post by listerdl on 2009-03-24
Have a look at my post: [http://ubuntuforums.org/showthread.php?t=1095851](http://ubuntuforums.org/showthread.php?t=1095851) I posted that a few days ago for pretty much the same thing.....

---

### Post by abeautifulplace on 2009-03-24
Thank you :)
But now, when I try and run conky, I get this error:
```
Conky: missing text block in configuration; exiting
```

---

### Post by mvalviar on 2009-03-24
What you are trying to do with those command is to move the sample conky configuration to .conkyrc. It seems that you created a .conkyrc file but it is empty. Go to your home folder and hit Ctrl-H to show hidden files. Find and open .conkyrc. You should be able to copy and paste conky config off the net on that file.

---

