---
title: "removing compiz screwed up things"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by duruttye on 2009-02-01
Hey guys, I just removed compiz and I can't restore the original performance and settings.
I am using a dell inspiron 1501 and ubuntu 7.10. With compiz removed, some icons are missing, like the disk mounter, the show desktop button.
 When I installed compiz, it installed xserver-xgl also. 
If I remove that, too, I can't connect to any network, wireless either.
Right now it is removed and when I scroll down this forum, it uses up my cpu like hell.
any suggestions?

thanx

using  VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]

---

### Post by Crafty Kisses on 2009-02-01
I'm not too sure what Compiz would have to do with your wireless network, but you can reinstall your Human icons by running the following command:
```
sudo apt-get install human-icon-theme
```
That should reinstall the icons. For your wireless, please post the results of these commands:
```
iwconfig
lshw -C network
```
Then either I or someone else can help you a bit further.

---

### Post by duruttye on 2009-02-01
I got the wireless and the icons back again, but it still uses a lot cpu when I view a page with flash, or java on it. I mean it is not like it was before. How can I find the proper driver so I can put it back.

The icons were restored, when I reinstalled the driver with envy.

Few examples:
when I minimize a window, it takes a lot more the before, and it uses a lot of cpu
in amarok, it takes long seconds to view it when an other application is minimized from in front of it. (makes any sense?)

so, any ideas?

---

### Post by duruttye on 2009-02-02
never mind, i had to reinstall the whole thing...


... where do I mark the thread solved??

---

