---
title: "Can't see firefox fonts in ubuntu"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by awiggin on 2009-11-09
Hi,

I tried looking for a solution to this, but I couldn't find one.  I just updated my ubuntu.  Then, when I restarted it and opened firefox, there was no text in the tool bar.  I can't see any text at all, either in the toolbar or in the address bar when I type in a URL.  

I can see text on the webpages themselves, but not on the application itself.

Please help!

Thanks,
wiggin

---

### Post by cariboo on 2009-11-09
You may have a corrupted Firefox profile, try pressing Alt-F2 and typing:

```
firefox -P
```

This will create a new profile, if it works, just transfer your bookmarks from the old profile and reinstall all the add-ons. You Firefox profile is located in 

```
~/.mozilla/firefox
```

---

