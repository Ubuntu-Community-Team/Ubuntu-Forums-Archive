---
title: "uninstall compiz-fusion"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Aksha on 2009-01-16
how do i completely uninstall all compiz-fusion components and revert back to normal ubuntu 8.10 settings?

---

### Post by abn91c on 2009-01-16
```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

---

### Post by HotShotDJ on 2009-01-16
> **Aksha said:**
> how do i completely uninstall all compiz-fusion components and revert back to normal ubuntu 8.10 settings?Compiz-fusion is included by default in Ubuntu, so it is part of the "normal ubuntu 8.10 settings."  I do not recommend un-installing this component, as it's removal may have unintended consequences.  Try using System --> Preferences --> Appearance.  Select the Visual Effects tab and check off "None."  This should get you back to default.

---

### Post by TransitMan on 2009-01-17
> **HotShotDJ said:**
> Compiz-fusion is included by default in Ubuntu, so it is part of the "normal ubuntu 8.10 settings."  I do not recommend un-installing this component, as it's removal may have unintended consequences.  Try using System --> Preferences --> Appearance.  Select the Visual Effects tab and check off "None."  This should get you back to default.

Actually, this is not entirely correct.
While compiz-fusion is installed as part of Ubuntu, it can be safely removed, either through Synaptic or through ```
sudo apt-get remove compiz
```
There is no harm in this and the OS will function just fine without it.

Now for how I know, I've removed compiz from both 8.04 and 8.10 with no ill effects.

---

