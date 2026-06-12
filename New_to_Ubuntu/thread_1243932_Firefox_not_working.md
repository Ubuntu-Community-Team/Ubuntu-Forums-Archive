---
title: "Firefox not working"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by samh785 on 2009-08-18
after installing firefox-3.5 in synaptic, I can no longer use firefox-3.0 that came with the computer. I tried to uninstall the firefox-3.5 package, but it forced me to uninstall the firefox package as well. I want to use the original one to play quake live with, so this is important! :confused:

---

### Post by Buuntu on 2009-08-18
Just uninstall and reinstall, that should do the trick.  Under 9.04 it should install 3.0 by default.
```
sudo apt-get remove mozilla-firefox
sudo apt-get install mozilla-firefox
```

---

### Post by tonyr1988 on 2009-08-18
> **samh785 said:**
> after installing firefox-3.5 in synaptic, I can no longer use firefox-3.0 that came with the computer. I tried to uninstall the firefox-3.5 package, but it forced me to uninstall the firefox package as well. I want to use the original one to play quake live with, so this is important! :confused:

Are you wanting to remove Firefox 3.5? Try this:

[LIST=1]
[*]apt-get remove firefox-3.5 ("firefox" is just a metapackage, removing it won't hurt anything)
[*]Remove the repository that you are using to get Firefox 3.5 (from /etc/apt/sources.list, or the GUI).
[*]apt-get update
[*]apt-get install firefox
[/LIST]

This ***should*** re-link "firefox" to "firefox-3.0" instead of firefox-3.5.

---

### Post by samh785 on 2009-08-18
I still want to use firefox 3.5 though, I just want to use 3.0 to play quake live.

I uninstalled firefox and firefox 3.5. When I tried to install just firefox it automatically installed firefox 3.5. What's happening here?

---

### Post by tonyr1988 on 2009-08-19
> **samh785 said:**
> I still want to use firefox 3.5 though, I just want to use 3.0 to play quake live.

I uninstalled firefox and firefox 3.5. When I tried to install just firefox it automatically installed firefox 3.5. What's happening here?

Are you downloading firefox-3.5 from a repository? If you still have that repo in your /etc/apt/sources.list (or haven't done an apt-get update), then firefox --> firefox-3.5 instead of firefox --> firefox-3.0

What happens if you run firefox-3.0 from the console?

---

