---
title: "Firefox Problems"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by ian19jam on 2009-03-05
Please can I have some help. I have lost Firebox browser and therefore no access to Internet on Ubuntu.
A box comes up to say: XML Passing Error: undefined entity Location: chrome//browser/content/browser
Line Number 34. Column 1

The underneath in Red: z windows id:"main-window"

No idea what this means.

Also if I try to add Firefox programme I receive the following Switch to Symaptic package Manager to restore conflict. It conflicts with other installed software.

I unfortunately download some programmes from the Symaptic Manager in the list under A but no idea which one is the cause of the problem 

Please can some one kindly advise in simple terms.

---

### Post by peakshysteria on 2009-03-05
Try to start Firefox in safemode. Then disable all add ons. Close it down and then try to open it as you usually would. Then re-enable the addons one by one until you meet the problem once more. Then remove the addon.

Safe mode explained: [http://kb.mozillazine.org/Safe_mode](http://kb.mozillazine.org/Safe_mode)

See also: [Standard diagnostic - Firefox]("http://kb.mozillazine.org/Standard_diagnostic_-_Firefox")

---

### Post by khelben1979 on 2009-03-05
As a temporary solution until your Firefox is fixed, I suggest that you install [the Opera web browser]("http://en.wikipedia.org/wiki/Opera_web_browser") as a replacement. [Look here]("http://www.opera.com/browser/download/").

---

### Post by mkvnmtr on 2009-03-05
I would guess that yu will need to uninstall and reinstall. Go to the package manager. Look under status and see if Firefox is not broken. Then you can find it by typing firefox in the search box.
Remember there are about a half dozen other internet browsers in the package manager.

---

### Post by unutbu on 2009-03-05
The following link contains instructions which may (or may not) fix your firefox problem: [http://ubuntuforums.org/showpost.php?p=6818710&postcount=6](http://ubuntuforums.org/showpost.php?p=6818710&postcount=6)
If it doesn't work, it is easy to undo the changes.

To find out what packages you've installed recently, open a terminal (Applications>Accessories>Terminal) and type
```

grep installed  /var/log/dpkg.log 
```

---

