---
title: "ndiswrapper INVALID DRIVER but i know im right"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by templa edhel on 2008-01-14
ok i am sure this has been posted before but i didnt understand the answers i got. im trying to get ndiswrapper to work using [this]("http://www.ubuntu1501.com/2007/01/fixing-wifi-on-dell-1501.html") link. everything was going fine until i ran ```
sudo ndiswrapper -l
``` then it gave me ```
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)
bcmwl5.sys : invalid driver!

```i think i may have messed up on more then on place because of this but i followed it TO THE LETTER. if i get a answer i understand im going to start out on a fresh clean install and do the tutorial. thanks for any help.

---

### Post by csat on 2008-01-15
There are some steps you should follow in order to get ndiswrapper to work properly.  So, a very nice information you can get [=>here<=](http://ubuntuforums.org/showthread.php?t=297092) which I consider the best I've ever read.

---

### Post by kevdog on 2008-01-15
You cant install the driver twice -- and that is what you did!

---

