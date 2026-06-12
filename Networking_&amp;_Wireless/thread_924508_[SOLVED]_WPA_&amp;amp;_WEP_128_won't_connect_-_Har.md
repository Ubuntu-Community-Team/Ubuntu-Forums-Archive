---
title: "[SOLVED] WPA &amp;amp; WEP 128 won't connect - Hardy, using either WICD and Network Manager"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by mattgif on 2008-09-19
Here's my situation:
I can connect to unsecured and WEP 64 secured networks just fine.  WPA, WPA2 and WEP 128 bits won't give me an IP.

On my home network, I've discovered that if I set a static IP for myself in WICD it will appear as if I'm connected to the router, but I cannot ping the router or any website (by IP or name).  

If I don't set a static IP, WICD gets to the 'acquiring IP' stage, then fails.

My machine is a Dell 1420 running Ubuntu 8.04.  I'm currently using WICD 1.5.2 (using WEXT for WPA), but have the same problem using Network Manager, or editing /etc/network/interfaces.  I have NDISWRAPPER and WPASUPPLICANT installed.  My home network is set to broadcast the SSID, use DHCP, and uses both WPA and WPA2 (TKIP) concurrently.  I have no problems connecting with my Vista/XP machines.

My WPA-PSK passphrase does have a special character ('!'), but the problem occurs on networks with alphanumeric passphrases as well.  

I'd be happy to post iwlist/iwconfig or whatever else might be helpful if requested.

I really appreciate that people on this forum are willing to put in the time and effort to help total strangers with computer problems - so a big thanks to everybody who gives this issue some thought.

---

### Post by FiReSTaRT on 2008-09-19
Try converting the passphrase to hex and entering it as hex. Did the trick  for me. (Network Manager 0.7.0)

[http://centricle.com/tools/ascii-hex/](http://centricle.com/tools/ascii-hex/)  <-- ascii-hex converter

---

### Post by mattgif on 2008-09-20
Thanks for the suggestion, FiReSTaRT.  Unfortunately it didn't work though - putting in the HEX value of the key caused WICD to fail at the authentication stage.

---

### Post by FiReSTaRT on 2008-09-21
Sorry to hear it.. That was the only thing that worked for me after trying everything that this forum (and a few other places) had to offer. Now that I think of it, I'm also running the 0.7.0 version of the network manager.

---

### Post by DrJohn999 on 2008-09-21
Similar problem here (just posted at [http://ubuntuforums.org/showthread.php?t=926055](http://ubuntuforums.org/showthread.php?t=926055) before I saw this thread). In my case WPA works fine EXCEPT when there's a space in the key.

Entering the HEX equivalent doesn't work (Probably gets interpreted as ASCII). Question then is where is the key cached, and how to set it with HEX instead of ASCII (in the file itself).

-- DJ

---

### Post by mattgif on 2008-09-21
For anybody following this, I've also posted the same question on WICD's forums, here: [http://wicd.sourceforge.net/punbb/viewtopic.php?id=195](http://wicd.sourceforge.net/punbb/viewtopic.php?id=195).  If someone there finds a solution that works, I'll try to remember and post it back here.

Vice versa for a solution proposed here.

---

### Post by mattgif on 2008-09-21
Should've read the stickies more carefully.  Per [http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218), I created a Broadcom blacklist, and updated the kernel.  

Good things come to those who read...

---

