---
title: "safe eject volume on ubuntu 9.04?"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by al.adab on 2009-12-02
I noticed that in Ubuntu 9.10 two options appear if you right click on an external drive icon: 

- unmount volume
- safe eject (or something of the sort, can't remember exactly)

Can't run 9.10 on my machine, so I'm back to 9.04, where the "safe eject" option is not available. I'm using various external drives, and I've just noticed that the light on my SanDisk memory stick doesn't turn itself off if I click on unmount only. When I tried 9.10 on this machine, it did turn itself off if I clicked on "safe eject". 

If I click on unmount on 9.04, remove the SanDisk, and plug it in a different machine that runs on Windows, a message pops up, saying that "some loss of data might have occurred as the unit was not properly disconnected". 

Bottom line: is the "unmount volume" option perfectly safe? Does it really matter that the light on the unit doesn't turn itself off? Is it possible to add the "safe eject" option to 9.04 if either is problematic? 

Thanks.

---

### Post by ikt on 2009-12-02
> **al.adab said:**
> 
Bottom line: is the "unmount volume" option perfectly safe? Does it really matter that the light on the unit doesn't turn itself off? Is it possible to add the "safe eject" option to 9.04 if either is problematic? 

Thanks.

Heya,

[http://ubuntuforums.org/showthread.php?t=1301556](http://ubuntuforums.org/showthread.php?t=1301556)

> "Unmount" unmounts a single partition, "Safely Remove Drive" unmounts all partitions of that device.

For example if you have a removable hard drive with 2 partitions selecting "Safely Remove Drive" for one of them would unmount both partitions, so that the device can be safely unplugged from your computer.

"Eject" is for media that can actually be ejected, like CD/DVD drive. So it unmounts the media and then ejects it (quite important if you happen to have a slot drive without a physical eject button).

Safely remove also seems to:

> Safely remove turns off the power to the USB device, not necessarily needed But that is my choice with a ext HD.

It's also bugged at the moment:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/453072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/453072)

Unmount should be fine.

---

### Post by al.adab on 2009-12-02
Good to know :) thanks for the info!

---

