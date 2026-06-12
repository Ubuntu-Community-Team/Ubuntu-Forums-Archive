---
title: "ndiswrapper without internet connection"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by nomowindows on 2007-02-15
hello, i have a linksys wpc54gver2 wireless pcmcia card.  it has an acx111 chipset.  I cannot get it to work.  I have tried the bug fix to point to the 1.2.1.34 driver already in ubuntu, but that did not work.  I have been reading about ndiswrapper and would like to try this method. However, I cannot download it without internet access.  I saw one post about downloading the package only on another computer.  I see that option in the synaptic manager,but I dont see an option to save it somewhere specific. I dont know where it is saved normally. In the terminal I typed whereis ndiswrapper-utils and it responded ndiswrapper-utils: ,,not a big help. Please help me. Thank you in advance for your help.

---

### Post by Floppyjoe on 2007-02-15
It can be installed from the Ubuntu install CD by clicking on System/Administration/Synaptic Package Manager. Then click on Edit/Add CDROM. Then click reload. Then search for ndiswrapper.

---

### Post by nomowindows on 2007-02-16
Thank you very much for the reply. Finally got it working by switching to edgy,it works without any hacking.

---

### Post by Roasted on 2007-12-03
Not to jack an old thread... but it answered my question exactly. However, when I do a synaptic search, it reads that ndiswrapper as well as the utils are installed. But under system - admin - I don't see "Windows Drivers" or whatever.

Where in the world is Ndiswrapper if it's installed??

---

