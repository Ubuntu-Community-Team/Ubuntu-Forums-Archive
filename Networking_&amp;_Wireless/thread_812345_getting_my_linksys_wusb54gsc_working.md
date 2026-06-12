---
title: "getting my linksys wusb54gsc working"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by sugarfresh on 2008-05-29
i ran into a problem when trying to use this guide([http://ubuntuforums.org/showthread.php?t=400236&page=1](http://ubuntuforums.org/showthread.php?t=400236&page=1)) once i get to step 9 where in the terminal you type "sudo make install" i get this
"make: *** No rule to make target `install'. Stop."
can someone help me? i followed all the other steps with no problem

---

### Post by Milardo on 2008-06-11
I would try this-using hardy,open synaptic manager and make sure you check the cd option so it can install stuff from cd, search for ndis and install all those ndis that come up in the search. After installing them in adminstration go to windows wireless drivers. Have your 3 or 2 files from the linksys cd or the one from linksys website. The .cat, .sys, and .inf files. Install new driver the .inf file and next go to the top right icon that looks like a computer monitor. Right click the iconand make sure network and wireless are checked. Next left click it and click the option that is search or find new wireless network not the create or manual option. Now you can enter your wireless security settings and you can easily choose wpa/wpa 2 as well. It should connect pretty fast. I got high speeds as well. To disconnect and unplug adapter (if that is what you have) just uncheck wireless from the icon and then pull out the adapter. To connect to the same wireless network you just have to plug it back in and check wireless if not already checked. You should be connected in about 50 seconds or so. This worked for my linksys wusb54gc.

---

### Post by beartard on 2008-06-21
The basic info in that thread quoted is over a year old.  My WUSB54GC works with standard Ubuntu drivers.  I don't need ndiswrapper.  What advantage do you gain by using ndiswrapper?

That having been said, with the last few kernel updates, my connection has been flaky.  It will stay connected to my router, but both IRC and kopete (messenger) will disconnect at the same time, both reconnecting immediately.

---

