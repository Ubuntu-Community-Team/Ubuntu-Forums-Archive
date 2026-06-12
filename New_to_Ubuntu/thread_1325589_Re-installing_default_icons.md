---
title: "Re-installing default icons"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by j33zU5 on 2009-11-13
I was removing some of the icon themes that ubuntu came with because I didn't use them and apparently the icon theme effects the cursor. Is there a package that comes with all the default icons that I can download?

---

### Post by durand on 2009-11-13
Was it possibly [apt:ubuntu-artwork]("apt:ubuntu-artwork")? Try installing [apt:ubuntu-desktop]("apt:ubuntu-desktop"), which will install all the default programs again. If you do that in synaptic rather than clicking the link, you may be able to get an idea of what it will install.

---

### Post by j33zU5 on 2009-11-13
I marked both ubuntu-desktop and ubuntu-artwork for re-installation but it didn't work. If somebody packaged and uploaded their /usr/share/icons somewhere I could get the ones back that I deleted and I'm pretty sure that would fix it.

---

### Post by durand on 2009-11-14
Try this in a termnal (Applications > Accessories > Terminal):
```
find /usr/share/icons > icons_list.txt
```

In your home folder, you should have a file called icons_list.txt. Could you please upload that? I can compare that with mine to see which folders you need.

---

### Post by j33zU5 on 2009-11-14
I had a friend upload his icons for me, thanks for the help though.

---

