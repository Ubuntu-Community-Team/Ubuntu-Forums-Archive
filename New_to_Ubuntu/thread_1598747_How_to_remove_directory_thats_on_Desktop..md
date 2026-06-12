---
title: "How to remove directory thats on Desktop."
date: 2010-10-16
forum: New to Ubuntu
---

### Post by Jetso on 2010-10-16
Once I put a file on my desktop, so that I could easily cd to the directory and untar it. When I did, I just planned on moving it to a better location. Now it won't let me move it OR remove it. I tried running using ```
rm[CODE]
```[/CODE] in terminal to remove it but it says I don't have permissin, even when I put sudo in front.

---

### Post by garvinrick4 on 2010-10-16
Make it easy on yourself and use nautilus in root.
Hit Alt/F2 and in box type gksudo nautilus
You are now in root nautilus, go to desktop and throw it away.

---

### Post by Jetso on 2010-10-16
Aha! That worked. I wonder why it didn't work when I tried to remove it as root in terminal. Well problem solved! Thank you very much.

---

### Post by Clever_Username on 2010-10-16
I generally use rmdir to remove directories.

---

