---
title: "update problems"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by letsgomudkip! on 2010-05-03
I just updated my ubuntu to 10.4 but when it re started ubuntu it did not load any applications or anything it's just a blank screen... I have kubuntu as well and it loads just fine a little slow but everything is there. Does anyone have any suggestions to get my ubuntu back to normal.

---

### Post by GSF1200S on 2010-05-03
You are not alone- A LOT of users have had this issue with 10.04. Unfortunately, its not a one command fix. Its due to some changes made in the Ubuntu boot process, namely plymouth and problems with proprietary graphics drivers (and even some open source ones). The following doesnt work for everyone, but it has got some people going. Look at my first post on the first page in this thread:
[http://ubuntuforums.org/showthread.php?t=1466337](http://ubuntuforums.org/showthread.php?t=1466337)
I had to do this myself in order to boot 10.04 (luckily I had 9.10 installed on another partition).

If you dont know what partition Ubuntu is installed on, post the results of:
```
sudo fdisk -l
```
here and hopefully I can tell you.

---

