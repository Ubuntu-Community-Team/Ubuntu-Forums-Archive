---
title: "File sharing issue - streaming xvid video"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by arjones85 on 2007-10-05
Wireless network is 802.11g, Linksys WRT45G Version 8

I have a harddrive shared out over my wireless network on Laptop #1, running Windows XP. The HD is NTFS formatted.

Laptop #2 is Ubuntu 7.04, using ndiswrapper for my broadcom card. It is dualbooting with XP

I can access the shared drive effortlessly on laptop #2, and begin to play an XVid-encoded video. It will play perfectly for about 10 minutes or so, and then begin to stutter as if the network can't keep up.

"Connection Information" shows it is connected at 54mbps.

When running Windows on laptop #2 and streaming videos, it works perfectly, no issues and no stuttering.


I do not even know where to begin to try to fix this issue. Any ideas guys?


Thanks!

---

### Post by akshunj on 2007-10-05
So, I've had various streaming video issues with similar setups.  I'm not sure what part of the network architecture is the problem, but I have found ways to fix it.  If you're using Xine, pump up the video and audio buffers.  Way up.  I can't tell you what number your network needs, but the buffers compensate for unreliable network conditions.  The setting is in the Xine UI config screen.  Hope this helps!

--Akshun J

---

### Post by arjones85 on 2007-10-06
I looked around and the only thing I could find in the UI config screens is where you set the network speed.

Is that what you are referring to?

---

### Post by akshunj on 2007-10-10
> **arjones85 said:**
> I looked around and the only thing I could find in the UI config screens is where you set the network speed.

Is that what you are referring to?

First, change the GUI settings for your "configuration experience level".  Use the drop-down and change it to "master of the known universe."  Click Apply.

Then click the "engine" tab.  You'll see the buffers dialog near the top.  I'd try 5000 for audio and video, then see what you get.

--Akshun J

---

