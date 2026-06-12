---
title: "Firefox Corrupted"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by ericstrom on 2009-09-06
Having trouble with Firefox hanging up on videos. I run Jaunty and Firefox 3.5.  I've tried numerous things and nothing has worked. I'm now convinced Firefox is corrupted somehow. I want to wipe it clean and start with a completely new version.**** But I want to keep my bookmarks.

Could someone tell me an easy way to accomplish this (with minimal cryptic terms as I'm new to this)

Thanks in advance for your ideas and suggestions.

---

### Post by Penguin Guy on 2009-09-06
Firstly; YouTube on Linux is not quite as good as YouTube on Windows. Secondly; I believe that if you just [uninstall]("http://www.psychocats.net/ubuntu/installingsoftware") firefox and then reinstall it, it should keep your bookmarks - **check with somebody else first**.

---

### Post by frank002 on 2009-09-06
You might want to back up your bookmark folder just in case.  You might also want to go to Opera.com and download the Opera 10 version.

---

### Post by jordilin on 2009-09-06
Backup your .mozilla/firefox directory, remove it, and start firefox again to make a clean firefox profile.

---

### Post by cariboo on 2009-09-06
An alternative way to create a new profile is to open a terminal and type:

```
firefox -Profilemanager
```

then copy your bookmarks.html file from the old profile to the new profile.

---

### Post by lovinglinux on 2009-09-06
> **cariboo907 said:**
> An alternative way to create a new profile is to open a terminal and type:

```
firefox -Profilemanager
```

then copy your bookmarks.html file from the old profile to the new profile.

The bookmarks.html file does not contain the user bookmarks since Firefox 3.0. Bookmarks are now stored in the database places.sqlite and backups are stored as json files under bookmarkbackups folder. The bookmarks.html is a left-over, just kept for compatibility reasons.

> **ericstrom said:**
> Having trouble with Firefox hanging up on videos. I run Jaunty and Firefox 3.5.  I've tried numerous things and nothing has worked. I'm now convinced Firefox is corrupted somehow. I want to wipe it clean and start with a completely new version.**** But I want to keep my bookmarks.

Could someone tell me an easy way to accomplish this (with minimal cryptic terms as I'm new to this)

Thanks in advance for your ideas and suggestions.

I don't believe re-installing would help. Creating a new profile usually fix several issues, but in your case I'm not convinced it got corrupted, simply because no matter what I do I also have sub-par video experience, specially with flash and javascript players. 

I suggest you read the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). It contains all information you need to create new profiles, optimize firefox, fix most common issues and more.

---

