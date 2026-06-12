---
title: "Why I can't view You Tube?"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by lockalidiot on 2010-02-19
I love it that I can bother you, the most helpful bunch of people I know, when ever I need to! AND actually get help! When I grow up(in usage of linux rather than age) I will hopefully join you in giving advice rather than asking for it all the time!

To the point:

There is something wrong with either my browser options or flash plug-ins. You Tube claims that I have either Java-script turned off (which I don't even know how to turn off) or too old version of adobe flash/which is the same they offer for install..) I cannot watch any flash vids with neither of my browsers (chrome and firefox). What is wrong and how I fix it?

---

### Post by cogier on 2010-02-19
I think I offered some advice before. Can I suggest that you try loading the Sun Java software from the Repository. There are 2 of them.

May be that will help.

---

### Post by nothingspecial on 2010-02-19
```
sudo apt-get install ubuntu-restricted-extras
```

ought to fix it.

---

### Post by cogier on 2010-02-19
AND if that does not work. Look for the Opera web browser on line and down load it. I think it's very good and seems to come with everything needed.

---

### Post by SuperSonic4 on 2010-02-19
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by lockalidiot on 2010-02-19
Thank you for fast responses!

1. Sun Java already installed and updated.
2. Restricted extras already installed and updated.
3. Opera and I don't like each other. (I'll see to it if nothing else works)
4. nonfree installing now. We'll see. 

EDIT: nonfree had no effect.

---

### Post by arnab_das on 2010-02-19
just check if its all installed.  go to synaptic and check if the restricted extras package is installed. if u need a graphical guide i have one on my blog ([http://exploreubuntu.wordpress.com/2009/11/14/install-restricted-extras-for-ubuntu/](http://exploreubuntu.wordpress.com/2009/11/14/install-restricted-extras-for-ubuntu/))

do note, that sometimes, google chrome can be very buggy with flash. hence i would strongly recommend that you stick to firefox. also, visit the following page:

[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

and then and check if u can see the flash video. The page will also give u information about the version of flash u are having, if u have it installed.

---

### Post by lovinglinux on 2010-02-19
For 32bit see [this](http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2).

For 64bit see [this](http://ubuntuforums.org/showthread.php?t=1358591).

---

### Post by lockalidiot on 2010-02-19
Thank you all! Again the community has saved the day! Special thanks to lovinglinux as his post was held the solution.

---

