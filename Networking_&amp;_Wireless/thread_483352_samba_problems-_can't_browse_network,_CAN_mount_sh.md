---
title: "samba problems- can't browse network, CAN mount shares"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by degreseven on 2007-06-24
Hello, 
I am having some odd samba problems. I am not able to browse my windows network at all, I just get errors about not being able to connect. I am also not able to connect to shares using the "connect to server" tool, or using smb://. I am, however, able to manually mount shares with an fstab entry like this...

```
//10.1.1.2/public    /media/share      smbfs   guest,dmask=777,fmask=777,noauto  0 0
```

Which works just how I want it to except that it's very slow- about 500 KB/s on a gigabit lan. Note the noauto option in there. If I take that out so it mounts automatically on boot, my comp just hangs for like 30 seconds when gnome loads, then when I try to access the mount I get weird read errors. 

All other machines on the network (both windows & ubuntu) are able to do these things just fine, so I'm sure it's a problem with this machine. I have tried reinstalling samba with no luck. Does anyone have any ideas?

This is 7.04, with all the latest updates btw =)

Thanks in advance.

---

### Post by scrooge_74 on 2007-06-24
Firewall issues most likely

Check[ this]("http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138") it may give you some ideas

---

### Post by dmizer on 2007-06-24
smbfs is very slow and unreliable.  it's an older protocol.

try taking a look at my cifs howto in the second link of my sig.  it may solve your browsing problems too.

---

### Post by degreseven on 2007-06-24
Thank you dmizer! using cifs works great.
I know smbfs is older, but I used it for a long time with gentoo (just recently switched to ubuntu), and had very few problems at all with it. Certainly nothing like the problems I have been having. 

I didn't see anything in the guide about browsing though, and obviously just mounting a share hasn't changed anything with my browsing. Any ideas for that, or did I miss something in the guide?

---

### Post by dmizer on 2007-06-24
well, if you enabled wins and configured nsswitch as well as made sure that your ubuntu machine was a part of the same workgroup as windows, i was expecting that your problems would be solved.

frankly though ... i can't browse my shares at work because the workgroup name (created on an old win2000 server) has an illegal character in it.  works in windows, but i can't do squat in linux.

---

### Post by degreseven on 2007-06-25
My mistake, that did work. Restarting networking didn't seem to do the trick. I just needed a reboot.

Thanks again!

---

