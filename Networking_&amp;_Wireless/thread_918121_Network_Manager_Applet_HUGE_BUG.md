---
title: "Network Manager Applet HUGE BUG"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by de0xyrib0se on 2008-09-12
If "roaming mode" is disabled the VPN option is gone from the applet menu, this basically translates to not being able to VPN when you enter a static IP...just great!

Any ideas? It can be replicated fairly easy, just install the vpnc plugin for the network manager or the pptp one, when in "roaming mode" you would see a VPN option in the applet but if you change it to non roaming its gone.

This is even better than getting a permission error when trying to samba share a folder from the GUI, but i'll save that user functionality for another thread.

---

### Post by pytheas22 on 2008-09-12
Although I agree that NM has its share of bugs, I can't reproduce this one (I'm using whichever build of NM is current on Hardy).  I turned off roaming mode and enabled static IP (and got a connection), but my VPN connection was still available.  So I killed and restarted Network Manager with roaming mode still disabled, and VPN was still there.  So the bug must either lie somewhere else, or you're using an old version of NM or the NM VPN plugin.

---

