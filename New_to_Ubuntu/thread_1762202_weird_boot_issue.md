---
title: "weird boot issue"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by gene simmons on 2011-05-18
hi all,thanx in advance for any info on this issue,i have been using linux for almost a year starting with jolicloud and now ubuntu 11.04 and i love it.i worked quite hard installing a custom plymouth that was working great and looking great.i then installed multisystems so i could try a few dif distros on a usb stick.puppy linux is sooooo fun haha,anyways when i boot back into ubuntu after running off the usb stick my boot plymouth changes from the one i made to a much smaller plymouth in the far left screen that just says ubuntu and the 5 dots under it,its not in the center like normal,after a few more boots and i changed compiz preference from default to unity my plymouth came back but everytime i use the usb to boot when i go back to ubuntu my plymouth is gone,oh i also unintalled unity via the synaptic package manger.has anyone had this issue,thanx guys

---

### Post by fabricator4 on 2011-05-18
Hi are you mounting the same /home in both distros?  That's the main way booting one distro can mess with the config files in another - the config is often hidden files or directories in /home/username.

It's not recommended to share /home/username in this case - but you can use a different username.


Chris

---

