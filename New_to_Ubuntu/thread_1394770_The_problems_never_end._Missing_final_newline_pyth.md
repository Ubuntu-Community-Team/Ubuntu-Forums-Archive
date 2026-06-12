---
title: "The problems never end. Missing final newline python-xdg"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by Simest on 2010-01-31
Continue my saga from: [http://ubuntuforums.org/showthread.php?t=1393169](http://ubuntuforums.org/showthread.php?t=1393169) 

Yes I have an up and working system now. I am even typing posting this from it.

World of Warcraft works now. Woot.

I can not install software from the software center.

```

(Reading database ... 75%dpkg: unrecoverable fatal error, aborting:

 files list file for package 'python-xdg' is missing final newline

```

Synaptic also gives the same error along with apt. 

Another 1:30 in the morning post asking how do I fix this without reinstalling?

---

### Post by Simest on 2010-01-31
Just a day bump since Im sure it wasnt seen at that hour of the morning.

---

### Post by Psumi on 2010-01-31
it means that the file is missing the newline that goes at the end of every file. For example, when you open up a configuration file, usually there's a blank line at the very end after everything.

if a package is missing this, there isn't really anything, you, yourself, can do about it.

---

### Post by halitech on 2010-01-31
can you install it by opening a terminal and running
```
sudo apt-get install python-xdg
```

---

### Post by Simest on 2010-01-31
@Psumi

So theory would be if I went to found the file and put in the missing line it would be fixed?

If I have to reinstall an OS im going back to what works.

@halitech 
I tried at sudo apt-get reinstall install to avial.

---

