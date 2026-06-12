---
title: "close, minimise, and maximise buttons are on the left"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by Krayona on 2010-04-23
I updated to the latest release candidate last night and since then, all my close, minimise, and maximise buttons are on the left of all windows instead of the normal right. I cant seem to find location of setting to adjust this. Can someone point me in the right direction?
Thank you.

---

### Post by sisco311 on 2010-04-23
```
gconftool-2 --type string --set /apps/metacity/general/button_layout ":minimize,maximize,close"
```

or press Alt+F2 and run
```
gconf-editor
```
go to /apps/metacity/general/ and set the button_layout key's value to *:minimize,maximize,close*

---

### Post by Krayona on 2010-04-23
Thank you...that worked perfectly.

---

### Post by sisco311 on 2010-04-23
> **Krayona said:**
> Thank you...that worked perfectly.

You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

