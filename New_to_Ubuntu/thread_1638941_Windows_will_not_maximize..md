---
title: "Windows will not maximize."
date: 2010-12-06
forum: New to Ubuntu
---

### Post by nu2this2 on 2010-12-06
Recently installed 10.04 on a Gateway laptop. Had wireless internet connection issues. Thanks to this forum that problem was solved. Now that I can go online, I see that I cannot maximize or minimize. The minus sign and box icons are missing in the corner of the window.

Has anyone had this problem before?

---

### Post by jtarin on 2010-12-06
Alt+F2>gconf-editor>Apps>Metacity>right-hand pane>double-click "button layout" and enter   ```
menu:minimize,maximize,close
```

---

### Post by pricetech on 2010-12-06
Have you looked in the upper left corner instead of the upper right ???

---

### Post by nu2this2 on 2010-12-06
> **pricetech said:**
> Have you looked in the upper left corner instead of the upper right ???

:oops::oops::oops: Thanks-----------------duhhhhhhhh

---

### Post by nm_geo on 2010-12-06
> **nu2this2 said:**
> :oops::oops::oops: Thanks-----------------duhhhhhhhh
 
You can move them to the right using Jtarin's reply, but I would recommend learning to look left for awhile. You will get used to it...Believe me.

---

