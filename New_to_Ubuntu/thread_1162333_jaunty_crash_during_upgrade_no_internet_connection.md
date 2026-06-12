---
title: "jaunty crash during upgrade no internet connection"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by sherri kastraba on 2009-05-17
While upgrading from 8.1 to Jaunty, I had a power problem.  It appears as jaunty is installed, however, I cannot access the internet either wired or wireless.  Network device not managed.  I received a new 9.04 in the mail to try to correct the problem.  Can anyone help?  Thanks so much

---

### Post by Michael.Godawski on 2009-05-17
hi,

when you run this command in terminal, do you get any error messages?

```
sudo dpkg --configure -a
```

Perhaps you have to install the drivers for your wlan card?

Please post the output of this commands:

```
sudo lshw -C network
iwconfig
```

---

### Post by sherri kastraba on 2009-05-17
the error is b43-fcutter -- my driver for the wireless, right?  but I can't access the internet with the ubuntu computer, so I cant post.

---

