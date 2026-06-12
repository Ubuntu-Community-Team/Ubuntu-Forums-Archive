---
title: "internet still not connecting"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by AutumnPhoenix on 2010-05-03
Device: lenovo s10-2 netbook

I have obtained a wired connection

The hardware driver broadcam B43 downloads fine but dosn't allow me to connect
The hardware driver broadcam STA gives me this message
> Please have a look at the log file for details: /var/log/jockey.log

---

### Post by AutumnPhoenix on 2010-05-03
bump

---

### Post by anewguy on 2010-05-03
Please don't bump posts so quickly - this is an all volunteer forum, and people just aren't here all the time nor at ones immediate call.  Forum rules say to wait 24 hours before bumping a post.

With that said, I understand your frustration and wanting this to be going *now*.  I don't use your machine or the broadcom drivers, but let's start at the beginning:

- when you hard-wired, did you do an sudo apt-get update ?

- after doing that, did you unplug the hard-wired cable?

- then, did you look in System/Administration/Hardware Drivers for a restricted driver and enable it?

- after that, did you reboot and then check wireless?

Those are the first things I would do in that order.  However, we should probably see the output from the following first:

- lspci

- lsusb (*if* your wireless adapter doesn't show in the lspci output)

Also - did you by any chance try ndiswrapper or edit the blacklist.conf file prior to attempting to use these drivers?

I'm going to be busy for a while, so I'll check back in a few hours.

Dave ;)

---

