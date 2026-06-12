---
title: "Strange Broadcom wireless issue"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by gnomee on 2007-10-04
Okay after installing ndiswrapper I have found a way to make it connect but its strange.

If I boot up and try to connect to any wireless network that is present its 60% going to not work or  take FOREVER to connect.  

If I select connect to other wireless network and type in a bogus name like test and click connect then go back and click on the network I really want to connect to it instantly finds the AP and connects. 

Any ideas on why this is?  I'm new to Linux/Ubuntu and loving it but this is just a little tweak I'd like to fix.

---

### Post by noob12 on 2007-10-04
I've heard this from a few other users too so you're not alone, but I've never experienced it myself; it seems to have something to do with the driver not putting the device in Managed mode initially.  You can try to see if that helps (using **sudo iwconfig wlan0 mode managed**).

It may depend on which ndiswrapper and Windows driver versions you are using.  The HOWTO thread: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990) installs good recent versions for you.  I haven't had any problems with that on my 4311 / Dell 1390 card.

No clue about the real cause though.

---

