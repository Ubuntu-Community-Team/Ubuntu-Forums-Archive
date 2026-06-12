---
title: "Mozilla and plug in problems"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by rhawnied on 2010-04-18
Hi 

So I have to apologise if this information is posted elsewhere but I tried to figure it out and only made it worse. I went to this site [http://ubuntuforums.org/showthread.php?t=1414595](http://ubuntuforums.org/showthread.php?t=1414595) and tried to install what she has I am sure I did it wrong.  I also upgraded to the latest Firefox then did an upgrade for adobe plug-in here apt:adobe-flashplugin?channel=$distro-partner I don't know if that worked right.  

Well the whole thing had bigger problems.  So I have removed the plugin and now...  I don't really know.  I am sure I need to fix what I did to start with But I don't know how

If you need any more info let me know and you should probably tell me where to find it.  Thank you so much in advanced:oops:

---

### Post by marshmallow1304 on 2010-04-18
> **rhawnied said:**
> rhawnie@rhawniesplace:~$ apt-get remove --purge flashplugin-installer
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

That operation requires root privileges, which you can gain temporarily by using sudo, like so
```
sudo apt-get remove --purge flashplugin-installer
```
You will be prompted to enter your password.

Alternately, you could find flashplugin-installer in Synaptic and mark it for "complete removal".



As for Flash, are you on 32-bit or 64-bit?  If you're not sure,
```
uname -m
```
will tell you.

---

### Post by rhawnied on 2010-04-19
Ahh thanks from the "root" thing and how to remove it.  I am reading more on termials right now. :) probably a good idea.

After I typed uname -m all it said was i686

---

### Post by rhawnied on 2010-04-19
and I never thought to look in Synaptic for it. Duh

---

### Post by scottiw2000 on 2010-04-19
Have you got the flash plugin installed successfully now? I've always been able to install it fine just by going either through synaptic package manager or the ubuntu software centre. Just don't try to install more than one version of a flash plugin at the same time. They sometimes seem to conflict with one another. The one you probably want (if you're running a recent Ubuntu distribution) is called flashplugin-installer in synaptic. In Ubuntu Software Centre it's called "Adobe Flash Plugin". Other versions (like swfdec-mozilla) are trying to do the same job but don't seem to work as well right now.

---

### Post by e4uforums on 2010-04-19
It's also very easy to install flash 10.1 beta.  Depending on your system you may see an improvement in flash performance using the new version.

Here is the download:[URL="http://labs.adobe.com/downloads/flashplayer10.html"]
http://labs.adobe.com/downloads/flashplayer10.html[/URL]

Here are the install instructions (really just 1 copy and paste command):
[http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-1-beta-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-1-beta-in-ubuntu.html)

---

