---
title: "Java SDK"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by JP121 on 2010-06-24
Hi.

(I know this question was answered several days ago, but a search came to no avail.)

What do I need to download from the software manager to be able to program Java files?  A search is not coming up with anything.

Thanks.

---

### Post by doas777 on 2010-06-24
go to System-Administration-Software Sources. select the tab that says "Other Software" and check both the boxes for the Partner repositories. then close the software sources, and when asked, tell it to reload the list. once the list is reloaded you can follow these instructions to install the sun jdk:
[http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/)

---

### Post by thebigob on 2010-06-24
in a terminal:

```

 sudo apt-get install sun-java6-jdk

```

---

### Post by JP121 on 2010-06-24
Thanks to both you guys!

---

