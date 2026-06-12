---
title: "Unknown networking error in logs"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by Doc Hoss on 2008-06-18
I'm still pretty new to Linux and Ubuntu, but I can usually pick around and figure out what something means in the logs.  But I have a whole log basically filled with this error.
```
Jun 18 21:56:21 XXX-laptop NetworkManager: <information>^Iwpa_supplicant(9574): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Jun 18 21:56:21 XXX-laptop NetworkManager: <information>^Iwpa_supplicant(9574): Wireless event: cmd=0x8b06 len=8 
Jun 18 21:56:21 XXX-laptop NetworkManager: <information>^Iwpa_supplicant(9574): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Jun 18 21:56:21 XXX-laptop NetworkManager: <information>^Iwpa_supplicant(9574): Wireless event: cmd=0x8b06 len=8 
Jun 18 21:56:21 XXX-laptop NetworkManager: <information>^Iwpa_supplicant(9574): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP]) 
Jun 18 21:56:21 XXX-laptop NetworkManager: <information>^Iwpa_supplicant(9574): Wireless event: cmd=0x8b06 len=8 
```

Anyone know what this is?  I'm starting to get to the point where everything in Ubuntu works...now I want to start cleaning it up so it runs silky smooth.  The connection works fine, so what is this message?

---

### Post by Doc Hoss on 2008-06-21
Anyone have any ideas?  More of a nuissance than anything, but I'd like to have some nice pretty log files!

---

### Post by alastair on 2008-06-21
If you want pretty log files, stop running NM! Or at least filter its messages using syslog-ng (or similar). It is way too verbose and chatty (ridiculously so). I don't know what the above means - and suspect you'll have to ask the NM developers (mailing list) or read the code ...

Alastair

---

### Post by Doc Hoss on 2008-06-25
NM = Network Manger, right?  Still kinda new to this game...sorry I'm unsure.  What would be a good alternative to network manager?  I'm still weaning myself off the graphical way of doing things, and I have to switch wireless networks a lot, as I travel constantly for work (hotel wireless).  Any suggestions?  Thanks for your reply. 

If anyone out there happens to glance across this and know what it means, I'd still like to know.  Again, nothing serious, as everything seems to work...just curious.

---

