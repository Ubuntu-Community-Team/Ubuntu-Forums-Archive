---
title: "Server - need to check wlan0 status and reset as needed"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by anewguy on 2009-01-20
Due to something I haven't been able to track down yet, my server sometimes becomes disconnected from the network.  It uses a wireless connection (USB stick - Belkin F5D7050 v4 I believe).  If I remove the USB stick, wait a few minutes, then reinsert it to its little stand, the system goes through the initialization of the device and my wireless comes back up, making the server visible again on the network.

I'd like to either write a script or a program, which ever is needed, to check the status of wlan0 (perhaps a ping to some address?) and if it is down, restart it.

Any ideas on how to go about this?

thanks in advance!

Dave :)

EDIT:  I know how, via a script, to get the ping to my router and see the count.  What I really need is a way, via a script, to "restart" what in my case is the wlan0 interface.  Can I ifconfig wlan0 up in a script?

---

### Post by DezSP on 2009-01-22
> **anewguy said:**
> Can I ifconfig wlan0 up in a script?

If it's a bash/shell script you're writing, then you can use any command you like. You can then use crontab to run the script automatically every X minutes/hours/decades/etc.. My bash knowledge is limited but a bit of Googling should give you the syntax you need.

---

