---
title: "Small NdisWrapper problem"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by DizzyTech on 2007-01-22
I installed to NdisWrapper 1.34 and installed the bcmwl5 driver for my Broadcom 4311 wireless card in my Compaq Presario 5204VR. The wireless works, but only after pressing the button to turn it off and back on.  To explain, when I start Ubuntu, the network manager applet shows the connection button, and cycles.  Both circular lights (signaling the network, my PC and the router) are unlit. This continues until the connection times out.  If I press the wireless button to turn it off and then back on, nm-applet immediately connects to my wireless.

Note that I had installed NdisWrapper 1.28 (or something close) following a tutorial on the wiki, and it worked without change.  This time I installed 1.34, following the exact instructions.

This is not a huge problem, it's more of an inconvenience but I'd like it fixed either way.

---

### Post by compiledkernel on 2007-01-22
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy) 

Ive found in the past dealing with and using the bcm43xx-fwcutter package to work more conclusively with most of the bcm branch cards. Id try that before resulting to the use of ndiswrapper.

---

### Post by DizzyTech on 2007-01-22
I already have, that's why I'm using ndiswrapper in the first place (I had received many recommendations like yours). FWCutter worked, but then steadily decreased my speed after connecting, and used eth1 instead of wlan0.  NdisWrapper works, and flawlessly I add.  There's just this slight inconvenience.

---

### Post by discord on 2007-01-25
look here got it working and with network manager!

[https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983](https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983)

---

### Post by DizzyTech on 2007-01-27
What am I supposed to do?  I gathered from the report that I update NdisWrapper, but I already have the most recent version (installed from stable .tar.gz's).

[quote="ndiswrapper -v"]
utils version: 1.9
driver version:        1.34
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
[/quote]

I have a BCM4311 utilizing the Windows bcmwl5 driver.  I followed a tutorial on the forums that told me how to compile ndiswrapper and install.  The tutorial worked a first time.  I updated my kernel [well, tried], and reinstalled NdisWrapper from the same tutorial using the newest version.  The kernel had no real peformance improvements, so I rolled back to the 2.6.17-10-generic that came with Edgy, but kept the NdisWrapper.  I have since reinstalled (after complete uninstallation) and it still has the problem.  After I press the button off and on on my Presario, nm-applet immediately connects, and works blazing fast.

This is just an inconvenience at the most, but I think this is linked to a deeper-rooted problem.

---

### Post by DizzyTech on 2007-06-12
This still occurs in Feisty.  However, it's now twice as annoying because hibernate and standby works (hooray)!  I have to do the on/off just at the right time to get my wireless to connect on resume.

---

