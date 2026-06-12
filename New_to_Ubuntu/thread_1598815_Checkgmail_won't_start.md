---
title: "Checkgmail won't start"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by drmichael on 2010-10-17
Let me preface this by saying that I first installed and used Ubuntu 10.10 (first time on Linux, period) yesterday and don't quite know my way around yet.

I've been trying to get checkgmail to work, but it simply will not start up.  I even try running it from the terminal and absolutely nothing happens (no errors or anything; it just sits there).

I just installed Ubuntu 10.10 yesterday

Any help would be much appreciated.

---

### Post by TeoBigusGeekus on 2010-10-17
How did you install it?

---

### Post by rburkartjo on 2010-10-17
drm works fine for me

---

### Post by drmichael on 2010-10-17
> **TeoBigusGeekus said:**
> How did you install it?

I used the Ubuntu software center first.  After it not working, I uninstalled it and then reinstalled from the terminal using sudo apt-get install checkgmail.  I've uninstalled and reinstalled many times and sometimes after uninstalling, I've deleted all of the checkgmail folders. 

It seems to install just fine and I can even see it running in the System Monitor, but I don't see any kind of panel icon or configuration window.  And I don't know if there is supposed to be, but there isn't an option to add it if right click on a panel and go to "add to panel."


> drm works fine for me


What does this mean (I'm still new to Ubuntu and linux in general)?

---

### Post by vangelas on 2010-11-15
I had the same problem, using meerkat 64 bit. This is what i did
1) installed SVN (in terminal: sudo apt-get install subversion)
2) downloaded the "latest development version via SVN". In terminal: svn co [https://checkgmail.svn.sourceforge.net/svnroot/checkgmail](https://checkgmail.svn.sourceforge.net/svnroot/checkgmail) checkgmail
It's all on the checkgmail page: [http://checkgmail.sourceforge.net/#download](http://checkgmail.sourceforge.net/#download)
3) Updated ("checkgmail -update" in the terminal), and it works fine now.

Hope this helps

---

