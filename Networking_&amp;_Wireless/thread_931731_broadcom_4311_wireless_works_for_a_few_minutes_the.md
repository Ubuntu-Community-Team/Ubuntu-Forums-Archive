---
title: "broadcom 4311 wireless works for a few minutes then stalls"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by PearlStreet on 2008-09-27
I am using an Acer Aspire 3680 with a Broadcom 4311 wireless card.  I am running ndiswrapper as described here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

This used to work perfectly until my laptop died on me because of a failure in the power board.  After replacing the power board with an identical part, now I have a problem I can't find referenced anywhere else in the forums.

Basically, on reboot or return from hibernation, I can see all available wireless networks in network manager.  If I wait, and do not select any of the networks, then after a few minutes all the networks are gone from the list.  If I try to connect to my wireless network, one of two things happen:

Sometimes, the connection goes through and I can obtain an IP address and use the internet for a couple of minutes.  After that, the list of wireless connections shows only the connected network and the signal strength shows 0 bars.  The system monitor shows I am not sending or receiving packets.  The system log shows this message when the connection disappears:

No ProveResp from curret AP 00:1b:2f:e3:64:6a - assume out of range
Supplicant state changed: 0

In the other scenario, I am not able to connect at all, and the system log shows this message:

Old device 'eth0' activating, won't change.
last message repeated 6 times
Activation (eth0/wireless): association took too long (>60s), failing activation.
Activation (eth0) failure scheduled...
Activation (eth0) failed for access point (<access point>)
Activation (eth0) failed.
Deactivating device eth0.

After this, of course, no wireless networks show up in the network manager.

If anyone knows anything about this issue, please help.  I'm fresh out of ideas...

---

### Post by Flacker2 on 2008-09-27
I think there are some ubuntu/debian package drivers for that card on the internet some where...
whats you lspci output?

---

### Post by RavUn on 2008-09-27
This worked for me.  I believe I have the BCM4312 but it supposedly works for 4311 also.
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

I don't know how well it'll work since you've already configured ndiswrapper, but you could give it a shot.  I messed with ndiswrapper but chose to reinstall ubuntu so I could try what was suggested above on a fresh install (I had just previously installed ubuntu beforehand so I didn't have anything to lose, though).

---

### Post by PearlStreet on 2008-09-27
Update:

According to the information in the link above for setting up the Broadcom wireless with ndiswrapper, running the following...

```
sudo lshw -C network
```

should show module=ndiswrapper under configuration for the wireless controller.  In my case, this still shows module=ssb, even when it is working for a couple of minutes.  The author describes this as a bug in Hardy for which you can read more details here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197558]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197558")

When I follow his instructions to fix this error in Hardy, which I have copied below, I still get module=ssb.

```
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy
sudo rmmod wl
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44
```

I would guess this is part of the problem, but don't know how to get around it.  Thoughts?

---

### Post by PearlStreet on 2008-09-27
Thanks for the replies.

The lspci output is:
Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

Additionally, Re:RavUn, I tried this morning to use implement the solution you posted without any luck (probably as you mentioned due to the changes I made when configuring ndiswrapper).  I might have to give it a go again if this ndiswrapper issue can't be resolved, but I had this working with ndiswrapper in the past so I'm hoping it's a bit simpler.  Also, trying to avoid a re-install since ~70% of the hardware in my Acer 3680 is not supported by default in Hardy :-/

---

### Post by Flacker2 on 2008-09-27
go to ubuntu.cafuego.net and go to what ever version of ubuntu you have
then go to broadcom
get the drivers but NOT the fw-cutter you don't need it
you don't need ndiswrapper for this

---

