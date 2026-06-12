---
title: "ndiswrapper + AMD64 + vista"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by Bastaard on 2007-04-16
Hey guys,

My problem is the following: I have a 64bit AMD processor and would like to install 64bit Ubuntu (7.04). However, my wireless networking adapter (Speedtouch 121g drivers are [here]("http://www.thomson.net/TMS/Minisites/BAP/Templates/SubCategory.aspx?NRMODE=Published&NRORIGINALURL=%2fEN%2fHome%2fMiniSites%2fBAP%2fTelecom%2fSubCategory%2ehtml%3fcategory%3dDSL%2520Modems&NRNODEGUID=%7b90224E22-AD3D-4EB5-97B7-5558F14F156D%7d&NRCACHEHINT=NoModifyGuest&category=DSL%20Modems")) does not have linux drivers available and so I will have to use ndiswrapper. Now, I think I won't be able to use 64bit Ubuntu because 64bit ndiswrapper doesn't support 32bit windows drivers.

Is there any way for me to get this wireless dongle working in 64bit Ubuntu? I've thought of two possible ways myself: trying to use a 32bit version of ndiswrapper on 64bit Ubuntu, or trying to use the (64bit?) Vista drivers with the regular 64bit ndiswrapper. I don't think those ideas would work though. Any other ideas? Or should I just use 32bit Ubuntu?

Thanks!

Ps. Cross-posted this on x86 64bit forum - [click here]("http://ubuntuforums.org/showthread.php?p=2462125#post2462125")

---

### Post by Bastaard on 2007-04-20
edit: *oops wrong thread*

---

### Post by HokeyFry on 2008-07-19
Using 32 bit drivers on a 64 bit system does not work. If there are no Windows 64 bit drivers, you may be out of luck with that device. I would check the ndiswrapper list [here]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/") though and see if anyone has been able to get your particular device working under 64 bit linux.

Best of luck!

---

