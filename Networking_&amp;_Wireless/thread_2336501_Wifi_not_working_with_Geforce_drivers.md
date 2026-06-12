---
title: "Wifi not working with Geforce drivers"
date: 2016-09-08
forum: Networking &amp; Wireless
---

### Post by nanth on 2016-09-08
I Finally got my wifi up and running on my RNX-AC1900pce wifi card but since I installed the driver for my Nvidia Geforce GT 740 Graphics card the wifi stopped working. I installed the driver directly from the command line, I'm not sure what it was but it looked for the proper driver and installed it. Disabling the graphics card for testing is not possible since the motherboard has no video output slots so I have to go through the graphics card. It will sometimes connect when I first start my computer or if I deactivate and reactive networking but it drops the connection sometime later. So my question is how can I uninstall the driver without disabling the graphics card and then install the drivers so that it doesn't do this again?

Thank you in advance!

---

### Post by wildmanne39 on 2016-09-08
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here.  
doubt

I really doubt the video card driver caused this issue I am almost positive it is just a coincidence.
Thanks

---

### Post by Bucky Ball on 2016-09-08
Did you check in Additional Drivers before installing graphics drivers from a third-party? The correct driver may have already been there and saved you the effort, and possibly the complication. That installs with a couple of clicks from Additional Drivers. 

Please state which release and flavour of Ubuntu you are using.

---

### Post by carl4926 on 2016-09-09
I had this happen recently on an older Box, so reverted to Nouveau as that didn't matter in this instance.
I didn't debug it
But I suspect it is a new issue so an older version of the nvidia blob might help if you can manage that

---

### Post by nanth on 2016-09-09
Solved I'm sorry to all of you who took the time to post here. After twiddling around with it it now works. I just needed to restart my pc a few more times.

 Thank you all for your time.

---

### Post by Bucky Ball on 2016-09-09
Great. Please mark the thread as solved to help others. See Thread Tools at top of page or the link in my signature. Thanks.

---

