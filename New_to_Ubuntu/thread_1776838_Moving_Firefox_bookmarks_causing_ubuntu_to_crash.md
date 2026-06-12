---
title: "Moving Firefox bookmarks causing ubuntu to crash"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by hoxzyk on 2011-06-06
Hello,

When i try to move a bookmark on the bookmark tool bar within firefox, ubuntu will crash to a blank black screen.

I had this issue on both firefox 4 and 3.5

I am using Ubuntu 10.4.

I found this thread but it didn't seem to be resolved, 

[http://ubuntuforums.org/showthread.php?t=896921](http://ubuntuforums.org/showthread.php?t=896921)

Does any one know how to fix it.

Happy Regards,
Hoxy

---

### Post by lovinglinux on 2011-06-07
[Optimize your databases]("http://www.webgapps.org/tutorials/firefox/optimization/database-optimization"). If that doesn't solve your problem, then make a backup of your bookmarks through the bookmarks manager, close Firefox and delete the file *places.sqlite* from your Firefox profile, located under ~/.mozilla/firefox/<profilename>/.

---

