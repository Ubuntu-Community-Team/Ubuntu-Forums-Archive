---
title: "No Network after resume from suspend"
date: 2016-05-07
forum: Networking &amp; Wireless
---

### Post by spandey on 2016-05-07
I have installed Ubuntu Mate 16,04 in an old PC. After resume from suspend there is no Network. Network manager icon just trying to connect.. 

In 14.04 I have to include Network Driver name in Suspend modules

/etc/pm/config.d/unload_modules
SUSPEND_MODULES="$SUSPEND_MODULES via-rhine"

How to do the same in 16.04?

---

### Post by spandey on 2016-05-10
After Googling found a solution,

> sudo modprobe via-rhine

fixes the network but the system won't shutdown after couple of suspend and resume !!!!

---

### Post by seanos on 2016-05-21
I had this problem a while back and it seems to have resurfaced (after a kernel update?). I found I had a script called wakenet which just contains [FONT=courier new]sudo nmcli nm sleep false[/FONT] to wake up network manager.

Edit: I&#8217;m still on 14.04.4 BTW.

See also: [Wireless networking not working after resume in Ubuntu 14.04]("http://askubuntu.com/questions/452826/wireless-networking-not-working-after-resume-in-ubuntu-14-04") for a more permanent solution.

---

