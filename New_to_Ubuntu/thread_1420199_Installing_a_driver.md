---
title: "Installing a driver"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by baddnady23 on 2010-03-02
Could someone walk me through step by step on how to install this driver for a garmin GPS?  Thanks!

[http://http://www8.garmin.com/support/download_details.jsp?id=209]("http://www8.garmin.com/support/download_details.jsp?id=209")

---

### Post by overdrank on 2010-03-02
Hi and it would appear that driver is for windows. Are you trying to use it with Ubuntu?

---

### Post by hansdown on 2010-03-02
Hi baddnady23.

This is for linux.

[http://www.gpspassion.com/FORUMSEN/topic.asp?TOPIC_ID=121878](http://www.gpspassion.com/FORUMSEN/topic.asp?TOPIC_ID=121878)

---

### Post by baddnady23 on 2010-03-02
Ok thank you. When I try to install Viking, i get the following message.  


Any ideas?

---

### Post by Mark20 on 2010-03-03
Looks like a dependency problem.  You can use apt-get build-dep to solve dependency issues, it's quite handy.  Try the following then re-install viking.

```
sudo apt-get build-dep viking
```

---

### Post by 3rdalbum on 2010-03-03
Why aren't you just using Viking from the repositories?

---

### Post by baddnady23 on 2010-03-03
Thanks Mark20!  That did the trick!

---

