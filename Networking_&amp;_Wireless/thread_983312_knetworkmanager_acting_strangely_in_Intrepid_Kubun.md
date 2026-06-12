---
title: "knetworkmanager acting strangely in Intrepid Kubuntu"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by Wisp558 on 2008-11-15
Now, I've gotten my D-Link WUA-1340 towork before, but now my knetworkmanager is going screwy. I have a WPA2 Personal security going, using the TKIP encryption. This is good.

Now, when I go into the Wireless configuration, I go in and choose the "Expert Settings", point it directly at WPA2, and tell it to only use the TKIP connection encryption type. Okay.

I save (or save and connect, I tried both), and it doesn't change. It doesn't seem to have remembered the settings I put in there. 

Does anyone have any ideas as to te origin of this internet-slaying oddity?

~Wisp558

---

### Post by Wisp558 on 2008-11-15
UPDATE:

It decided to connect, but it still doesn't seem to be holding any changes...

---

### Post by djgobby on 2008-12-03
I am also having this issue. I have Kubuntu 8.10 running on my laptop which has the INPROCOMM IPN2220 wireless card and uses ndiswrapper to function. I tried at first to connect with the standard settings which didn't work, so I went into advanced and specified the settings. This still didn't work straight away but at some point during that day it suddenly 'kicked in'. Since then it's back to not working and it doesn't remember the specified settings.

I apologise in advance for being an absolute Linux noob and if there are any spelling errors due to missing letters, my keyboard is worn out.;)

---

### Post by checho4 on 2008-12-19
I've been having the same problems on my Dell Inspiron 1501.  It looks like KNetworkManager was rushed out, so there was little time to fix the bugs.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279262](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279262)

I have yet to find the solution, but I'm sure it's in there somewhere.  Will post if I find something that works.

---

### Post by checho4 on 2008-12-20
You have to remove the network-manager and network-manager-kde packages.  From there, you can manage your networking with the command:
```
sudo ifup eth0
```

---

