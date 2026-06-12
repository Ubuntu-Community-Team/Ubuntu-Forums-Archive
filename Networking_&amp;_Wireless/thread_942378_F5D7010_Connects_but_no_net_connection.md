---
title: "F5D7010 Connects but no net connection"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by EdwardFisher on 2008-10-09
Hello.
Sorry if this has been done to death. I have searched but non of the posts seem to answer my question.
I have just followed this tutorial for installing the windows drivers for the Belkin F5D7010xx wireless card. 
[http://ubuntuforums.org/showthread.php?t=187004&highlight=Belkin+54g+F5D7010](http://ubuntuforums.org/showthread.php?t=187004&highlight=Belkin+54g+F5D7010)
I used the drivers packaged at the bottom of the page and the whole install went swimmingly. 

ndiswrapper -l 
shows that the belkin driver is installed and the device is connected. When i click on manual wireless config i put in the correct network details.

But for some reason i am unable to connect to the network. Wireless config mentions i have 100% signal so its recieving the signal ok. 
Im wondering if there is a problem with encryption.
The wireless network is setup with AES and KTIP encryption however there isnt an option on the manual wireless config for the exact one. So i used WPA2 (same as KTIP?)

Anyways so today on my windows machine i installed the windows driver again (I know this works as i use it every day). Found the correct driver in the windows driver directory and coppied this.

Im at work at the moment but do you think this will help, possibly the driver in the tutorial is old seeing as its from 2006!

Cheers.
Ed

---

### Post by maxhavoc on 2008-10-09
If you control the WAP you might want to try disabling encryption to see if that allows you to connect. Of course that's a temporary solution, but at least it allows you to identify the problem. If encryption is the issue then you need to configure which protocol WPA2 uses. It can do either TKIP or AES-CCM. Some routers annoyingly call it TKIP+AES or some variation thereupon. Can you post exactly what encryption is being used on both the router and your Wireless NIC config?

---

