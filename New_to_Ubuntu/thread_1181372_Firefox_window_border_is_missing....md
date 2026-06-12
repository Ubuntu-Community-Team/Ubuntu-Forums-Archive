---
title: "Firefox window border is missing..."
date: 2009-06-07
forum: New to Ubuntu
---

### Post by taminrob on 2009-06-07
Wondering if someone can help...in surfing the web today, at some point my Firefox window border has disappeared and the window covers my top panel as well...so the top of the screen shows the "file edit view" etc.  I can close the window in the file menu and if I hit f11 twice, it will return to normal, but when I open Firefox again, I have the same issue.  It only happens with Firefox.  This occured as best I can tell after hitting one of those annoying websites that hijacks the browser and tries to keep you from leaving or closing the browser.

Any suggestions on how I can set this back to normal??

Thanks

---

### Post by lovinglinux on 2009-06-08
Delete the file *localstore.rdf* from your Firefox profile.

> 

Deleting localstore.rdf will reset your customized toolbars, window positions and sizes, tree sort orders, and similar settings. A new file will be created on start up or when the application first needs to write to the file.

Before deleting this file, saving a screen capture (print screen) could prove useful in implementing customizations to restore former appearance after this file is recreated. 

[Related article](http://kb.mozillazine.org/Corrupt_localstore.rdf) [kb.mozillazine.org]




*UKeywords: 649167 2009 june localstore.rdf firefox profile f11 fullscreen*

---

### Post by taminrob on 2009-06-08
Thank you for the quick reply and the information...that was exactly what I needed, everything is back to normal now.

---

