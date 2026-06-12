---
title: "Flash apps online won't load"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by Onlyonebanjo on 2009-05-22
I've been using 9.04 (and Linux in general) for about three weeks now, and I'm slowly finding Ubuntu replacements for all my previous XP dependencies. One thing I can't seem to work out is some sites I go to that won't load their flash apps. A prime example is [www.conceptispuzzles.com]("http://ubuntuforums.org/www.conceptispuzzles.com"). All the puzzles there are flash-based, but they do not appear when I'm in Ubuntu. Plus, they're some awesome puzzles.

I have the restricted extras package installed, and most other sites will work. Another post I read suggested making sure I had the right plugin selected, such as Adobe. If that's the case, how do I check that it's selected?

---

### Post by majamba on 2009-05-22
download the flash adobe player from the adobe website
make sure you get the .deb package for ubuntu 8.04 +
when selecting what type to download

then install the package it should work fine with firefox

---

### Post by Onlyonebanjo on 2009-05-22
I did that, but I'm still just seeing a blank white space instead of a puzzle.

Also, nothing on Vimeo will play--just a white space too.

---

### Post by clhsharky on 2009-05-22
Cool puzzle! Bye

---

### Post by Onlyonebanjo on 2009-05-22
Okay, well, anyone else?

---

### Post by Drokles on 2009-05-22
I have the same problem. Well, not all flash-apps are plain whiteness. Youtube works (well sort of anyway). Adobe flash player doesn't appear as a firefox plugin even though I've tried installing it a few times.

---

### Post by rob2uk on 2009-05-22
You need to make sure you're not using any other Flash plugins (such as IcedTea), then use the following command

```
sudo aptitude update
sudo aptitude install flashplugin-nonfree
```

This downloads the plugin, installs it and adds it to Firefox

---

### Post by gandaran on 2009-05-22
> You need to make sure you're not using any other Flash plugins (such as IcedTea), then use the following command

icedtea in the open-java plugin not flash.
 
Onlyonebanjo
ensure you don't have any open source flash plugin like swfdec and gnash installed and only one adobe flash plugin either the flashplugin-nonfree or adobe-flashplugin not both, they are the same thing, those puzzle games work fine with adobe flash.

---

### Post by Onlyonebanjo on 2009-05-22
Thanks for all the advice guys. I found this [article]("http://ubuntuforums.org/showthread.php?t=766683") later last night and it contained a sudo command that purged all my flash plugins and reinstalled only Adobe, which fixed the problem. Sorry I didn't reply sooner that the problem got worked out.

```
sudo apt-get purge adobe-flashplugin flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree
```

---

### Post by rob2uk on 2009-05-22
> **gandaran said:**
> icedtea in the open-java plugin not flash.


Yeah, my bad. Sorry!

---

### Post by DaveySpeedstar on 2009-07-27
Sorry I'm late but I've just picked up on this thread.  

You might want to check out category5.tv, as there is a script there which installs all the video codecs (and more besides)

[http://www.category5.tv/content/view/164/77/](http://www.category5.tv/content/view/164/77/)

---

