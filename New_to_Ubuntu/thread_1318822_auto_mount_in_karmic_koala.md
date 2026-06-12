---
title: "auto mount in karmic koala"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by patchido on 2009-11-07
well, i had a partition automatically mounted in jaunty, but i followed the same steps and i cant manage to make it work, is there any difference? or how should i do it?

---

### Post by pastalavista on 2009-11-07
You'll need to edit your /etc/fstab file. I could explain how to that but the easiest way is to install 'pysdm' Storage Device Manager. ```
sudo apt-get install pysdm
``` It will be in the System-> Administration menu after install.

---

### Post by stinkeye on 2009-11-08
--

---

### Post by Elcid247 on 2009-11-22
pysdm messes with fstab which is quite a mess.

i did 2 tutorials about this,

[old 1]("http://o-saad.blogspot.com/2009/10/automount-in-karmic.html")

[new 1]("http://o-saad.blogspot.com/2009/11/better-automount-rules-in-karmic.html")

---

