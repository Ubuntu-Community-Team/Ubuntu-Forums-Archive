---
title: "Help with uploading ndiswrapper and windows wireless driver"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by officialj03 on 2007-05-24
I have a Compaq R3000 laptop running Win XP, and I managed to get Ubuntu running alongside it with no problems. The Ubuntu 7.04 works fine except for connecting to the internet wireless.  When I plug an ethernet cable from my wireless router, I have no problem accessing the internet.  The Ubuntu forums talks about wireless cards and how ndiswrapper can be used to help in accessing the internet. However, my laptop has a built-in wireless capability, and as of now Ubuntu doesn't seem to recognize any of the networks around.  In fact, the wireless light on the side of the laptop doesn't light up even when press it.  I guess Ubuntu needs ndiswrapper along with my Windows driver to activate the wireless on my laptop.  

My question do I need to download "ndiswrapper" in the first place.  And if have to do so, how do I upload it alongside the windows driver as mentioned in the Help documentation to my computer.  Last time I downloaded ndiswrapper and tried messing around with it I failed miserably.  Please help.

---

### Post by ugm6hr on 2007-05-26
If your wireless card is not recognised, it is feasible that you need ndiswrapper.  Best to use *lspci* in Terminal and see what chipset the card uses (it should be labelled Network or Ethernet controller).

Then search for that chipset in these forums - there might be a specific How To in here.  Or rename the thread with the chipset - someone might help.

If you find you do need ndiswrapper - in Feisty:

1. Open Synaptic Package Manager and search for *ndisgtk* and then mark this (and other recommended bits) for installation.
2. Go to Windows Wireless driver editor (or whatever it's menu entry is) and then chose to add a new driver - and just open the *driver*.inf file (which should be part of the Windows driver).
3. Edit /etc/modules and add *ndiswrapper* to the bottom of it and press return (you need to be root to do this)
4. Reboot, and it should theoretically work.

To see whether your card is ndiswrapper compatible, and which Windows driver to use, check this:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

---

