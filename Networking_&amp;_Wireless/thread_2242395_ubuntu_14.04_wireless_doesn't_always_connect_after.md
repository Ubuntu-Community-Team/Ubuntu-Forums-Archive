---
title: "ubuntu 14.04 wireless doesn't always connect after suspend"
date: 2014-09-01
forum: Networking &amp; Wireless
---

### Post by jon.ti on 2014-09-01
I've got a frustrating intermittent problem with wireless access.  Using Ubuntu 14.04 with the MATE desktop the machine suspends OK, but when I resume it does not always reconnect to my wireless router.  The wired ethernet connection still works just fine.  Logging out and logging back in does not solve the problem, nor, alarmingly, does a reboot help.

When wireless connectivity has been lost, if I login to the Unity desktop there is still no wireless connection. But I've been able to get it working again in Unity after much thrashing around by deleting the wireless connection a few times (!) and reentering the details, but there doesn't seem to be a clear procedure for restoring wireless connectivity.  I just have to keep trying various different options. Once I've re-established wireless connectivity in Unity, I can log out and login to the MATE desktop and then the wireless manager reconnects OK. Very odd.

I've run the wireless trouble shooting script and the output is attached.  I'd very much appreciate some help in resolving what looks to be some kind of intermittent bug in my networking setup.

---

### Post by jon.ti on 2014-09-01
oops, wireless-info.tar.gz attached this time, I hope!

---

### Post by jon.ti on 2014-09-01
[ATTACH]256049[/ATTACH]

Yay! third time lucky!

I should have mentioned I ran the above report while the wireless was refusing to connect.

---

### Post by weatherman2 on 2014-09-01
Invalid attachment...

---

### Post by jon.ti on 2014-09-01
[ATTACH]256051[/ATTACH]

I don't know why the previous attachment was invalid, but this one (same file) seems to work OK.

---

### Post by jon.ti on 2014-09-01
This output from nm-tool in wireless-info.txt looks important> ##### nm-tool #####

** (process:4125): WARNING **: Could not create object for /org/freedesktop/NetworkManager/Settings/1: uid 1001 has no permission to perform this operation

** (process:4125): WARNING **: handle_property_changed: failed to update property 'available-connections' of object type NMDeviceWifi.

** (process:4125): WARNING **: error: cannot retrieve connection: uid 1001 has no permission to perform this operation

---

### Post by weatherman2 on 2014-09-01
Looks like you are using the Mate desktop? [Sorry, didn't notice that in initial post.]  Could be related to that.  I am not familiar with Mate.  I use Gnome Flashback with my 14.04 installation and i don't have Network Manager files in that path at all.

---

### Post by jon.ti on 2014-09-01
Yes, it's the desktop I settled on for this machine, my new-to-me Dell Latitude D631 laptop, after  installing 11 (including quite a few Gnomes) different desktops.  I'm  running gnome-session-fallback on my two desktop machines.

I do get the feeling that the problem is somehow related to Mate. I've tried to recover the connection in Mate and in Unity, and only ever succeeded from Unity.

---

### Post by jon.ti on 2014-09-04
I take back what I said about my MATE desktop, it turns out it's working flawlessly.  Apologies to Martin Wimpress.

I ran the wireless diagnostic script again, this time when the wireless connection was working OK, and compared it with the original from when the wireless had "stalled" and was not reconnecting after a suspend.  I used Meld, a great program for comparing files.

The only significant difference was shown by the dmesg section. The stalled wireless was timing out on authentication, so I figured I'd give the router as little to do as possible, and cleared client IP settings from it. That helped a lot. It also seems to help to have the connection *not* automatically connect, but to do it 'manually'.

There's still rare occasions when I lose the wireless connection. I've found that plugging in the ethernet cable and waiting half an hour or so restores things to normal.

---

