---
title: "[SOLVED] web folder is a web page?"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by secondstage on 2008-04-14
I've noticed on web sites that when you go to [http://www.website/](http://www.website/) or a URL without a file name at the end, you open up a web page. Yesterday I installed apache2, and gnump3d, and it would be nice to have a homepage open instead of an 'index of' page.

PS It's Apache 2.2.4, and gnump3d 2.8. Also, when I tried to install php4, it said that one of the dependencies was unavailable (same with php5).

---

### Post by aeiah on 2008-04-14
it will look for index.html by default. place that in your /var/www folder and it should display it when someone goes to your ip

---

### Post by secondstage on 2008-04-14
That has always puzzled me. Thank you

---

