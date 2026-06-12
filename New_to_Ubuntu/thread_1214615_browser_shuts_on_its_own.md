---
title: "browser shuts on its own"
date: 2009-07-16
forum: New to Ubuntu
---

### Post by shadowseeker on 2009-07-16
Hiya people,new to ubuntu and to linux so have many questions,forgive me is this is already in the forums somewhere but I'm typing this from my blackberry and can't check to see if it has.
I have been running firefox and it keeps shuting itsslf down at certain times,I have not worked out if it is anything particular yet but thought I would post it on here to see if its a common occurance or not.
I'm running ubuntu 9.14 I think it is,after switching from xp and apart from this browser problem it seems like a good system to use.

---

### Post by lisati on 2009-07-16
> **shadowseeker said:**
> Hiya people,new to ubuntu and to linux so have many questions,forgive me is this is already in the forums somewhere but I'm typing this from my blackberry and can't check to see if it has.
I have been running firefox and it keeps shuting itsslf down at certain times,I have not worked out if it is anything particular yet but thought I would post it on here to see if its a common occurance or not.
I'm running ubuntu 9.14 I think it is,after switching from xp and apart from this browser problem it seems like a good system to use.

I haven't had Firefox shut down for no apparent reason. Are you sure it's version 9.14 of Ubuntu you're using? the numbering scheme is based on the year and the month it's released.

---

### Post by Elep.Repu on 2009-07-16
> **shadowseeker said:**
> Hiya people,new to ubuntu and to linux so have many questions,forgive me is this is already in the forums somewhere but I'm typing this from my blackberry and can't check to see if it has.
I have been running firefox and it keeps shuting itsslf down at certain times,I have not worked out if it is anything particular yet but thought I would post it on here to see if its a common occurance or not.
I'm running ubuntu 9.14 I think it is,after switching from xp and apart from this browser problem it seems like a good system to use.

I hope you mean Ubuntu 9.04.

Try ```
sudo apt-get --purge remove firefox; sudo apt-get install firefox
```

Purge doesn't remove your /home settings so you should be fine after that.
If not post back.

---

### Post by shadowseeker on 2009-07-16
Thanx I'll give that a go when I get in tonight and let ya know how it goes

---

