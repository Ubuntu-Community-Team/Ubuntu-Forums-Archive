---
title: "Update Manager Glitch"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by Grey Ham on 2010-12-28
:KS

When my Update Manager prompts and I "check" for new updates they show up, as per usual.  Then I click on "Install Updates" and it is as if I clicked on "check" again.  Then I try and click on "Settings.." and again it is as if I have click on "check".  I currently have 493.7 MB of updates to do.... this has been a problem for awhile.  Suggestions?  Thanks

---

### Post by Sef on 2010-12-29
1) What version of Ubuntu are you using?

2) Applications > Accessories > Terminal

then copy and paste the code below into the Terminal:

```
sudo apt-get update && sudo apt-get upgrade -y
```

Copy and paste any errors here.

---

