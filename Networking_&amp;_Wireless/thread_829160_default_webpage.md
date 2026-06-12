---
title: "default webpage"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by cedrik on 2008-06-14
I use Apache 2.2.8, i set up 3 virtual hosts on it. everything works fine but when I type localhost in my web browser, it directs me to the webpage of one of my hosts. how do I change the settings so that it would direct me to a directory I specified?

---

### Post by aysiu on 2008-06-14
Don't include an index.php or index.html file in that directory?

---

### Post by lswb on 2008-06-14
If the web server is running on the box where you are typing "localhost" into the address bar, then this is normal and expected behavior. What are you actually trying to access when you type in localhost? If you just want to view a local file (or directory) then either use the File/Open File menu, or type in something like
  file:///path/to/DirectoryName
in the address bar.

---

