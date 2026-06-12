---
title: "Can I SSH into a Laptop if it is not logged in?"
date: 2020-06-04
forum: Networking &amp; Wireless
---

### Post by stevermann on 2020-06-04
I have an old laptop where I installed Ubuntu 18. It's a place that I can experiment with various things before committing them to my main NUC.  If I screw the OS up, I just reinstall it and all I've lost is some time.  Whereas if I screw up my NUC then my Plex server, my NAS folders and weeks of work are lost.

Here's my question.
The laptop goes to sleep after a period of unuse and the current user is logged out.  But, when this happens, I can't log in by SSH.

Is this normal?  Can I turn off the auto logoff on the laptop?

---

### Post by The Cog on 2020-06-04
I don't know what a NUC is, but it sounds to me as though you should look seriously at getting some kind of backup arrangement in place for it.

No it is not normal to lose remote ssh access when the local user logs out. The listening ssh process is a daemon, and should be running all the time the computer is running. Could it be that the laptop is going into suspend mode, where all processes are stopped until some external event (e.g. tap the power button again) waked it up? There are settings for this under power management. I can't say exactly where because I'm on Xubuntu, but they are under settings somewhere. Maybe suspend after a period of inactivity is the default for laptops.

---

### Post by TheFu on 2020-06-04
If the machine is running AND the network is on AND you know the current IP, then yes, you can ssh into the machine.

However, 
if the laptop goes to sleep, you cannot.
if the laptop turns off the networking to save power, you cannot.
if the storage where the HOME directory is located for the userid the ssh connection is being made into, then you cannot (well, there are exceptions).

Some systems have a "wake on LAN" capability. This is when another system sends a special packet to the MAC address on the same subnet which can pull a system out of sleep (usually 5-35 seconds later) and then we can login.  I've never seen this work over wifi. It is an ethernet thing, not an IP thing, so both systems have to be on the same LAN, not going through a router, just a hub or switch. 

The motherboard, BIOS and network card all have to support this WoL feature.  Desktops commonly do these days.

I would be surprised if a NUC didn't support WoL when using a wired ethernet connection.
[https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)

---

### Post by stevermann on 2020-06-04
It's the Intel NUC.  I do have a robust backup plan for the NUC including offsite storage. but I like to experiment with new tools or things to try out before committing them to the NUC.
I thought the laptop was only setup to turn off the display and never go to into hibernation.  But, I'll check again.  Thanks

---

### Post by stevermann on 2020-06-04
Thanks. This laptop is so old it barely suppports WiFi or Ethernet.  I will investigate if the network adapter supports WOL.

---

