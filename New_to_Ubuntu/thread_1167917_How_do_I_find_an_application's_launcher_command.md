---
title: "How do I find an application's launcher command?"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by Robarooney on 2009-05-23
I am just getting started with Ubuntu linux.  I want to add a web editor application (screem) to my Applications menu.  I've opened the Create Launcher dialog box but I don't know what to put in the Command field.  I have Screem downloaded and I think it is installed.  So, what is the command that I need?  Thanks.

---

### Post by Mornedhel on 2009-05-23
Most likely "screem".

---

### Post by t0p on 2009-05-23
I take it you didn't install screem with apt-get or synaptic?  Because when I installed it with apt-get, it was added to my Applications menu automagically (under Programming).

To install it through apt-get, you type into a terminal

```
sudo apt-get install screem
```

and you should find it appear in the Applications menu.

But the versions of apps in the repos are sometimes quite old.  If you installed screem manually (manually downloading it from a website somewhere) you probably won't want to reinstall with apt-get.  In that case, you can find the path to the screem executable by typing into the terminal:

```
which screem
```

which will return the output

```
/usr/bin/screem
```

Put that in the command field and it should work fine.

---

