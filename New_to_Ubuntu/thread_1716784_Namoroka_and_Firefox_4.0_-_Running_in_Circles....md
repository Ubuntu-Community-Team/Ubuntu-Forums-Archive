---
title: "Namoroka and Firefox 4.0 - Running in Circles..."
date: 2011-03-28
forum: New to Ubuntu
---

### Post by Toronto11 on 2011-03-28
Hi everyone, I just wanted to get the new Firefox 4.0, but couldn't get it to install or at least I don't think I did so I went and tried to reinstall an old Firefox and now I have Namoroka.  I'm running 10.04

How do I get the 4.0 version and get rid of Namoroka?  Do I go into the etc files and delete the Firefox folders?  Will this delete my bookmarks and passwords?

While I'm here, am I missing something, but .tar.gz files don't seem to be easy to install for me.  I can extract the files, but then it's just a Firefox folder.  What do I do next.

And will using a command like sudo apt-get install Firefox-4.0 do anything?

I'm kind of new, but this .tar.gz file for Firefox has really got me running in circles.

---

### Post by Enigmapond on 2011-03-29
Very easy..
Open the terminal and do:

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update && sudo apt-get upgrade
```

This will upgrade FF4 right over Namoroka...

At least it did with me.. :)

Cheers!

---

### Post by rosencrantz on 2011-03-29
Hi toronto11,
don't install from tarball if there is a repository/.deb package available, and don't try deleting system folders, let the package manager or an uninstall script do that for you.
In your case, this howto will help: [http://www.ubuntugeek.com/how-to-install-firefox-4-in-ubuntu-using-ppa.html](http://www.ubuntugeek.com/how-to-install-firefox-4-in-ubuntu-using-ppa.html)
I'm not quite sure what you mean by having Namoroka, isn't that just the 3.6 release? In that case, updating to 4.0 will probably replace it. Your bookmarks and settings shouldn't be affected, they are in ~/.mozilla.
Cheers, rosencrantz

---

### Post by 23dornot23d on 2011-03-29
You are better off using a Deb file if possible ...... 

Search on - [Firefox 4 Deb 2011 mar]("http://www.google.com/search?client=ubuntu&channel=fs&q=+firefox+4+deb&ie=utf-8&oe=utf-8#sclient=psy&hl=en&client=ubuntu&hs=5I6&channel=fs&q=firefox+4+deb+2011+mar&aq=f&aqi=&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=904e06910588146f") or just click this link

---

### Post by Toronto11 on 2011-03-29
Thanks for the suggestions, I'll give them a shot.

---

### Post by Toronto11 on 2011-03-30
Solved!! Excellent, thanks for the help.

---

### Post by Enigmapond on 2011-03-30
Hey I got your message. No problem at all. Glad to help and glad it worked for you! Please mark this thread as solved in the "Thread Tools".. :D

Cheers!

---

