---
title: "Problems with .net 2.0"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by JPKnowMad on 2009-09-01
First off let me say I love ubuntu so far but I am a complete newbie and have no clue what I'm doing right now. I tried to install .net 2.0 from another thread. I used terminal and typed some http://  address, not sure what it was now. I was trying to download a reader from coursesmart to view an etextbook. Needless to say I couldn't get it. I uninstalled wine and the reader and when i restarted i get this message at login about $Home.dmrc is being ignored. I would like to completely get rid of .net and never going back to microsoft. Any help with this would be great. It is not causing any recognizable problems in the running of the system but I would just like to fix it so I can have my nice new ubuntu back. Thanks for the help. by the way, i have the jaunty 9.04 i believe it is. Sorry for my lack of ubuntu knowledge. I'm working on it though. Thanks again

---

### Post by matsuzine on 2009-09-01
Hi, JPKnowMad.

First, a couple of questions.  You say you tried to install .net 2.0 using wine.  This may be tricky as I'm not sure how robust .net 2.0 is in wine.  Here are a few ideas:

This thread seemed to get it to install.  No idea how stable it is...

[http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/a749c4252a8f9a57](http://groups.google.com/group/comp.emulators.ms-windows.wine/browse_thread/thread/a749c4252a8f9a57)

You might also consider trying your app on mono 2.0, which is the open source implementation of .net for multiple platforms including linux.  I've found that some apps work, some just don't work on mono.  But it's straightforward to install and run.  You can find it in the repositories.

---

### Post by superzorro on 2009-09-01
Hi, I don't know if this could help you but below you will find the appdb page at Wine for .net 2.0, with common errors and troubleshooting:

[.net 2.0 Wine appdb]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3754")

Also, I have read that you probably can use .net apps with wine, and the safest method could be installing it through winetricks:

Here is the page:

[http://wiki.winehq.org/winetricks]("http://wiki.winehq.org/winetricks")

Hope you can fix your system

---

### Post by JPKnowMad on 2009-09-01
Thanks guys. I didn't install .net with wine. I installed with winetricks from terminal. Now I am just looking for a way to reverse the changes. I no longer want .net framework on my system. I already removed wine but I am still getting the $HOME.dmrc is being ignored at login. I just want to fix that error and remove the microsoft crap. Thanks again.

---

