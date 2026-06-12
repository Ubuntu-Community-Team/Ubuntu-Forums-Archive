---
title: "Cannot open Firefox"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by seymur on 2010-03-07
I couldn't start Firefox from applications menu, or from icon in dockbarx. I restarted and tried again, still the same result; It was not opening at all.
Then I searched in the forum, and tried one [solution]("http://ubuntuforums.org/showthread.php?t=286331").
I did this;

```
Okay ... open terminal and cd to /usr/bin

sudo rm firefox

sudo ln -s /usr/bin/firefox/firefox firefox
```

After I did this, the following message shows up when I open Firefox;
[INDENT]Could not launch 'Firefox Web Browser'
Failed to execute child process "firefox" (Too many levels of symbolic links)[/INDENT]

I guess "sudo ln -s /usr/bin/firefox/firefox" changed the path for firefox. I checked in /usr/bin, there is a firefox file, it has a red cross on it, and when I open it it says The Link 'firefox' is Broken.
There is another file "firefox-3.5", when I run it nothing's happening.

I have already backed up .mozilla folder.
Please help me, what should I do, reinstall Firefox and replace my back-up folder? I just don't want to lose all the extensions and customizations.

---

### Post by seymur on 2010-03-08
Removed firefox from Ubuntu Software Center and installed it again. Firefox now opens, and all my add ons and bookmarks are in place.

---

