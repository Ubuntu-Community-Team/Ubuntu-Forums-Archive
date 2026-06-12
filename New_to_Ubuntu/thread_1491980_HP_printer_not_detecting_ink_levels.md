---
title: "HP printer not detecting ink levels"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by kapi on 2010-05-24
Tried using a hp printer I had sitting in the garage. Still using 9.10 and it works fine (didn't in Jaunty).

Now I cant seem to get ink levels to show up. it says 'Marker levels are not reported for this printer'

any ideas?

---

### Post by yaaarrrgg on 2010-05-25
Might depend on the printer.  For my HP monochrome laser printer, I just downloaded the latest hplip from source forge, and ran it.  Then the toner levels were in the hplip toolkit.

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

HP's site should say what level of support the printer model will have... what's the model?

---

### Post by kaibob on 2010-05-25
My experience is the same as that of yaaarrrgg. The only difference is that I installed hplip-gui from the repo's to get the HPLIP toolbox. In my case, the total install including dependencies was around 75 MB. I have included a screenshot of the toolbox.

---

