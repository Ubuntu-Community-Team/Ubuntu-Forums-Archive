---
title: "KDE apps fonts are scrambled after upgrade to  Jaunty"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by nemodot on 2009-05-05
Hi, I'm having this problem since the upgrade to Jaunty. 

I attached a screenshot to show you how badly KDE apps look like now.

I couldn't find a solution to this problem yet. There's a bug submited in launchpad but it isn't solved there either.

---

### Post by kpkeerthi on 2009-05-05
Press ALT+F2 and enter **qtconfig**. There you can change the fonts of QT apps. It might help.

---

### Post by nemodot on 2009-05-05
It doesn't help. :(

---

### Post by kpkeerthi on 2009-05-05
> 
Workaround:
   1. exit all qt applications,
   2. go into &#8220;System>Preferences>Appearance>Fonts&#8221;,
   3. change VRGB/BGR to RGB/BGR.

... from [https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/334657]("https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/334657")

---

