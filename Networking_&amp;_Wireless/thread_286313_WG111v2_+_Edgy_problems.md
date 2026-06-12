---
title: "WG111v2 + Edgy problems"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by b-dizzle on 2006-10-27
I use a WG111v2 USB dongle to connect to my wireless network.  I had followed [this tutorial]("http://www.ubuntuforums.org/showthread.php?t=212365&highlight=wg111v2"); wrapped the driver, blacklisted some things, had it working like a charm.

Then I installed Edgy, and it doesn't work.  ndiswrapper -l says the driver and hardwear are present, but the network manager doesn't recognise it.  It shows up on the device manager, but not as a wlan0 interface.

Any ideas?  Should I maybe un-blacklist the things I blacklisted before?  If all else fails, is there a way I can revert to Dapper?  Internet connection is pretty crucial on this computer, and wired connection is out of the question.

Thanks in advance.

---

### Post by acegolfer on 2006-10-27
I'm using WG511. I had to comment out (enable) the "auto wlan0" and the next line in /etc/network/interfaces to work with network manager in Edgy. I know it's different from Dapper. Tell me whether it works.

---

### Post by b-dizzle on 2006-10-28
Nope, didn't work.  Auto wlan0 was already enabled, and my ESSID, WEP key, static ip and such were already in there under auto wlan0.  I think the problem is that Ubuntu isn't recognising that my WG111v2 is a wlan0 gateway... but I don't know how to fix that.  I'm gonna start from scratch and unload the NDISwrapper drivers and then try that from the beginning.  

Any help is appreciated **greatly**.

---

### Post by b-dizzle on 2006-10-28
I got it working... I have to boot up in the old version of the kernel for some reason or another, but it works when I do.  If someone finds out how to make it work in the new one, let me know, but for now I'm happy.

---

